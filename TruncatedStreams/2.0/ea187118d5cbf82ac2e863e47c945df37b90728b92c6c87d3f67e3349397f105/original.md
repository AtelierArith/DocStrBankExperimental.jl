```
SentinelizedSource(io, sentinel) <: TruncatedSource
```

A truncated source that reads `io` until `sentinel` is found.

```jldoctest sentinelio_1
julia> io = IOBuffer(repeat(collect(0x00:0x0f), 2));

julia> sio = SentinelizedSource(io, [0x0a, 0x0b]);

julia> read(sio)
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

julia> eof(sio)
true
```

As soon as a read from a `SentinelizedSource` object would read the start of a byte sequence matching `sentinel` from the underlying IO stream, EOF is signalled, potentially leading to an `EOFError` being thrown.

```jldoctest sentinelio_1
julia> read(sio, Int)
ERROR: EOFError: read end of file
[...]
```

Seeking works as if the stream ends at the first byte of the sentinel: backwards seeking will always succeed if the wrapped stream allows it, and forward seeking will only seek up to the sentinel. Note that forward seeking will consume bytes from the wrapped stream.

```jldoctest sentinelio_1
julia> seek(sio, 8); read(sio)
2-element Vector{UInt8}:
 0x08
 0x09
```

Detection of eof can be reset with the `Base.reseteof()` method. Use this if the sentinel that was read is determined upon further inspection to be bogus.

```jldoctest sentinelio_1
julia> Base.reseteof(sio)  # that last sentinel was fake, so reset EOF and read again

julia> read(sio)  # returns the first sentinel found and continues to read until the next one is found
16-element Vector{UInt8}:
 0x0a
 0x0b
 0x0c
 0x0d
 0x0e
 0x0f
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
```

!!! note
    If the wrapped stream does not contain a sentinel, reading to the end of the stream will throw `EOFError`.


```jldoctest sentinelio_3
julia> io = IOBuffer(collect(0x00:0x07)); sio = SentinelizedSource(io, [0xff, 0xfe]);

julia> read(sio)
ERROR: EOFError: read end of file
[...]
```
