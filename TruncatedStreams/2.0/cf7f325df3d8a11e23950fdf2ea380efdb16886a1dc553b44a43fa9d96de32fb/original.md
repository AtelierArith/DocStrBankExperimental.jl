```
FixedLengthSource(io, length) <: TruncatedSource
```

A truncated source that reads `io` up to `length` bytes.

```jldoctest fixedlengthio_1
julia> io = IOBuffer(collect(0x00:0xff));

julia> fio = FixedLengthSource(io, 10);

julia> read(fio)
10-element Vector{UInt8}:
 0x00
 0x01
 0x02
 0x03
 0x04
 0x05
 0x06
 0x07
 0x08
 0x09

julia> eof(fio)
true
```

As soon as a read from a `FixedLengthSource` object would read past `length` bytes of the underlying IO stream, EOF is signalled, potentially leading to an `EOFError` being thrown.

```jldoctest fixedlengthio_1
julia> read(fio, Int)
ERROR: EOFError: read end of file
[...]
```

Seeking does not affect the length at which the stream is truncated, but may affect how many bytes are available to read.

```jldoctest fixedlengthio_1
julia> seek(fio, 8); read(fio)
2-element Vector{UInt8}:
 0x08
 0x09
```
