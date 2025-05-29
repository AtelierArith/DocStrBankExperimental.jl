```
BGZFCompressorStream(io::IO; threads=nthreads(), compresslevel=6)
```

Create a `TranscodingStream` which block-gzip compresses data from the underlying `io` with the given `compresslevel`. The stream will compress up to `threads` block concurrently.
