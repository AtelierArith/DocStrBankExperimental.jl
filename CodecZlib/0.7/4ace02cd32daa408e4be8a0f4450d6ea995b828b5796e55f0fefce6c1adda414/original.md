```
ZlibCompressor(;level=-1, windowbits=15)
```

Create a zlib compression codec.

## Arguments

  * `level` (-1..9): compression level. 1 gives best speed, 9 gives best compression, 0 gives no compression at all (the input data is simply copied a block at a time). -1 requests a default compromise between speed and compression (currently equivalent to level 6).
  * `windowbits` (9..15): size of history buffer is `2^windowbits`.

!!! warning
    `serialize` and `deepcopy` will not work with this codec due to stored raw pointers.

