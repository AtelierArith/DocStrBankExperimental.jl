`BufferedInputStream{T}` provides buffered reading from a source of type `T`.

Any type `T` wrapped in a `BufferedInputStream` must implement:

```
BufferedStreams.readbytes!(source::T, buffer::Vector{UInt8}, from::Int, to::Int)
```

This function should:

  * refill `buffer` starting at `from` and not filling past `to`.
  * return the number of bytes read.

Failure to read any new data into the buffer is interpreted as eof.
