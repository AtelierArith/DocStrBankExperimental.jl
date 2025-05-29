```
GzipDecompressor(;windowbits=15, gziponly=false)
```

Create a gzip decompressor codec.

If `gziponly` is `false`, this codec can decompress the zlib format as well.

## Arguments

  * `windowbits`: size of history buffer (8..15)
  * `gziponly`: flag to inactivate data format detection
