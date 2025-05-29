```
GzipDecompressor(;windowbits=15, gziponly=false)
```

Create a gzip decompressor codec.

If `gziponly` is `false`, this codec can decompress the zlib format as well.

## Arguments

  * `windowbits` (8..15): Changing `windowbits` from its default of 15 will prevent decoding data using a history buffer larger than `2^windowbits`.
  * `gziponly`: flag to inactivate data format detection

!!! warning
    `serialize` and `deepcopy` will not work with this codec due to stored raw pointers.

