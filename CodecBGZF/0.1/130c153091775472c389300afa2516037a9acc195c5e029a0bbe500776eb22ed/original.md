```
BGZFDecompressorStream(io::IO; threads=nthreads())
```

Create a `TranscodingStream` which decompresses block-gzipped data from the underlying `io`. The stream will compress up to `threads` block concurrently.
