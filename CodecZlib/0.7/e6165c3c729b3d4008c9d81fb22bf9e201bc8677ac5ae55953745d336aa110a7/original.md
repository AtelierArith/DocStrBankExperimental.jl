```
ZlibDecompressor(;windowbits=15)
```

Create a zlib decompression codec.

## Arguments

  * `windowbits` (8..15): Changing `windowbits` from its default of 15 will prevent decoding data using a history buffer larger than `2^windowbits`.

!!! warning
    `serialize` and `deepcopy` will not work with this codec due to stored raw pointers.

