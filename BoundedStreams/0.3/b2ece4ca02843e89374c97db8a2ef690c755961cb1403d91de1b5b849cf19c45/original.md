```
BoundedInputStream(source::IO, nbytes::Integer; offset=0, close=nbytes)
```

Provide the `IO` interface for reading the source stream `source`. Restrict the number of bytes to to `nbytes`. A `BoundedInputStream` can be considered as a view on the wrapped stream, which starts at the position of that at the time of creation, and extends by the given size. Trying to read beyond this area throws `EOFError`.

The optional integer argument `offset` shifts the starting point off the current position of the source stream.

The optional argument `close` determines the position of the source stream after this stream is closed. The special value `BoundedStreams.CLOSE` closes the source stream in this case.
