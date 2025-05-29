The Avro.jl package provides a pure Julia implementation for reading writing data in the [avro format](http://avro.apache.org/docs/current/spec.html).

### Implementation status

It currently supports:

  * All primitive types
  * All nested/complex types
  * Logical types listed in the spec (Decimal, UUID, Date, Time, Timestamps, Duration)
  * Binary encoding/decoding
  * Reading/writing object container files via the Tables.jl interface
  * Supports the xz, zstd, deflate, and bzip2 compression codecs for object container files

Currently not supported are:

  * JSON encoding/decoding of objects
  * Single object encoding or schema fingerprints
  * Schema resolution
  * Protocol messages, calls, handshakes
  * Snappy compression

### Package motivation

Why use the avro format vs. other data formats? Some benefits include:

  * Very concise binary encoding, especially object container files with compression
  * Very fast reading/writing
  * Objects/data must have well-defined schema
  * One of the few "row-oriented" binary data formats

### Getting started

The Avro.jl package supports two main APIs to interact with avro data. The first is similar to the JSON3.jl struct API for interacting with json data, largely in part due to the similarities between the avro format and json. This looks like:

```julia
buf = Avro.write(obj)
obj = Avro.read(buf, typeof(obj))
```

In short, we use [`Avro.write`](@ref) and provide an object `obj` to write out in the avro format. We can optionally provide a filename or `IO` as a first argument to write the data to.

We can then read the data back in using [`Avro.read`](@ref), where the first argument must be a filename, `IO`, or any `AbstractVector{UInt8}` byte buffer containing avro data. The 2nd argument is *required*, and is the type of data to be read. This type can be provided as a simple Julia type (like `Avro.read(buf, Vector{String})`), or as a parsed avro schema, like `Avro.read(buf, Avro.parseschema("schema.avsc"))`. [`Avro.parseschema`](@ref) takes a filename or json string representing the avro schema of the data to read and returns a "schema type" that can be passed to `Avro.read`.

The second alternative API allows "packaging" the data's schema with the data in what the avro spec calls an "object container" file. While `Avro.read`/`Avro.write` require the user to already know or pass the schema externally, [`Avro.writetable`](@ref) and [`Avro.readtable`](@ref) can write/read avro object container files, and will take care of any schema writing/reading, compression, etc. automatically. These table functions unsurprisingly utilize the ubiquitous Tables.jl interface to facilitate integrations with other formats.

```julia
# write our input_table out to a file named "data.avro" using the zstd compression codec
# input_table can be any Tables.jl-compatible source, like CSV.File, Arrow.Table, DataFrame, etc.
Avro.writetable("data.avro", input_table; compress=:zstd)

# we can also read avro data from object container files
# if file uses compression, it will be decompressed automatically
# the schema of the data is packaged in the object container file itself
# and will be parsed before constructing the file table
tbl = Avro.readtable("data.avro")
# the returned type is `Avro.Table`, which satisfies the Tables.jl interface
# which means it can be sent to any valid sink function, like
# Arrow.write("data.arrow", tbl), CSV.write("data.csv", tbl), or DataFrame(tbl)
```
