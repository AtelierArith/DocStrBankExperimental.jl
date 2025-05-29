```
Noop()
```

Create a noop codec.

Noop (no operation) is a codec that does nothing. The data read from or written to the stream are kept as-is without any modification. This is often useful as a buffered stream or an identity element of a composition of streams.

The implementations are specialized for this codec. For example, a `Noop` stream uses only one buffer rather than a pair of buffers, which avoids copying data between two buffers and the throughput will be larger than a naive implementation.
