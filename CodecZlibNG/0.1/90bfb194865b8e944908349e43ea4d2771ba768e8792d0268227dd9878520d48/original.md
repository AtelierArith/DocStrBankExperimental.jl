```
DeflateCompressor(;level=-1, windowbits=-1)
```

Create a deflate compression codec.

## Arguments

  * `level`: compression level (-1..9)
  * `windowbits`: size of history buffer (8..15)
  * `memlevel`: memory size used for internal compression state (1..9)
  * `strategy`: compression strategy

      * 0 <-> Z*DEFAULT*STRATEGY
      * 1 <-> Z_FILTERED
      * 2 <-> Z*HUFFMAN*ONLY
      * 3 <-> Z_RLE
      * 4 <-> Z_FIXED
