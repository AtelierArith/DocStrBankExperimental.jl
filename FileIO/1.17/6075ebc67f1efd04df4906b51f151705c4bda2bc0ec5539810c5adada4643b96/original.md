`FileIO` API (brief summary, see individual functions for more detail):

  * `format"PNG"`: specifies a particular defined format
  * [`File{fmt}`](@ref) and [`Stream{fmt}`](@ref): types of objects that declare that a resource has a particular format `fmt`
  * [`load([filename|stream])`](@ref): read data in formatted file, inferring the format
  * `load(File{format"PNG"}(filename))`: specify the format manually
  * [`loadstreaming([filename|stream])`](@ref): similar to `load`, except that it returns an object that can be read from
  * [`save(filename, data...)`](@ref) for similar operations involving saving data
  * [`savestreaming([filename|stream])`](@ref): similar to `save`, except that it returns an object that can be written to
  * `io = open(f::File, args...)` opens a file
  * [`io = stream(s::Stream)`](@ref stream) returns the IOStream from the query object `s`
  * [`query([filename|stream])`](@ref): attempt to infer the format of `filename`
  * [`unknown(q)`](@ref) returns true if a query can't be resolved
  * [`skipmagic(io, fmt)`](@ref) sets the position of `io` to just after the magic bytes
  * [`magic(fmt)`](@ref) returns the magic bytes for format `fmt`
  * [`info(fmt)`](@ref) returns `(magic, extensions)` for format `fmt`
  * [`add_format(fmt, magic, extension, libraries...)`](@ref): register a new format
  * [`add_loader(fmt, :Package)`](@ref): indicate that `Package` supports loading files of type `fmt`
  * [`add_saver(fmt, :Package)`](@ref): indicate that `Package` supports saving files of type `fmt`
