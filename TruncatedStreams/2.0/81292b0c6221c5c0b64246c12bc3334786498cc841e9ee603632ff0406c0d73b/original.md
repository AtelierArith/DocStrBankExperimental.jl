```
TruncatedSource <: IO
```

Wrap an IO object to read only as much as should be read and not a byte more.

Objects inheriting from this abstract type pass along all read-oriented IO methods to the wrapped stream except for `bytesavailable(io)` and `eof(io)`. Inherited types *must* implement:

  * `TruncatedStreams.unwrap(::TruncatedSource)::IO`: return the wrapped IO stream.
  * `Base.eof(::TruncatedSource)::Bool`: report whether the stream cannot produce any more bytes.

In order to implement truncation, some number of these methods will likely need to be implemented:

  * `Base.unsafe_read(::TruncatedSource, p::Ptr{UInt8}, n::UInt)::Nothing`: copy `n` bytes from the   stream into memory pointed to by `p`.
  * `Base.read(::TruncatedSource, T::Type)::T`: read and return an object of type `T` from the stream.
  * `Base.bytesavailable(::TruncatedSource)::Int`: report the number of bytes available to read from   the stream until EOF or a buffer refill is necessary.
  * `Base.seek(::TruncatedSource, p::Integer)` and `Base.seekend(::TruncatedSource)`: seek stream to   position `p` or end of stream.
  * `Base.reset(::TruncatedSource)`: reset a marked stream to the saved position.
  * `Base.reseteof(::TruncatedSource)::Nothing`: reset EOF status.
  * `Base.peek(::TruncatedSource[, T::Type])::T`: read and return the next object of type `T` from the   stream, but leave the bytes available in the stream for the next read.

The following methods *must* be implemented by the wrapped IO type for all the functionality of the     `TruncatedSource` to work at all:

  * `Base.eof(::IO)::Bool`
  * `Base.read(::IO, ::Type{UInt8})::UInt8`

The wrapped stream also must implement `Base.seek` and `Base.skip` for seeking and skipping of the truncated stream to work properly. Additionally, `Base.position` needs to be implemented for some implementations of `Base.seek` to work properly.
