```
VirtualOffset(stream::BGZFDecompressorStream)
```

Obtain the `VirtualOffset` of the curret position of `stream`. If `stream's` input stream is seekable, seeking to this offset will leave the stream in an equivalent state to its current state. A `BGZFDecompressorStream` only tracks the offset of the 16 previous blocks. If more than 16 blocks are stored in `stream`'s output buffer, this operation will fail.
