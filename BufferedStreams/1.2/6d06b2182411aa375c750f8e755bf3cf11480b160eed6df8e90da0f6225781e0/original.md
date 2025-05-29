`BufferedOutputStream{T}` provides buffered writing to a sink of type `T`.

Any type `T` wrapped in a `BufferedOutputStream` must implement:

```
BufferedStreams.writebytes(sink::T, buffer::Vector{UInt8}, n::Int, eof::Bool)
```

This function should:

  * write `n` bytes from `buffer`, starting at the first position
  * `eof` is `true` when there will be no more write operations to `sink`, to facilitate flushing or closing the sink, etc.
  * `writebytes` should return the number of bytes written. This must be `n` or 0. A return value of 0 indicates data should not be evicted from the buffer.

The buffer passed to this function never reallocated by `BufferedOutputStream`, so it's safe to retain a reference to it to, for example, report some bytes as written but do so lazily or asynchronously.
