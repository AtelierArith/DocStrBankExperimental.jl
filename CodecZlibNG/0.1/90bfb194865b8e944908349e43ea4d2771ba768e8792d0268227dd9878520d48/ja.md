```
DeflateCompressor(;level=-1, windowbits=-1)
```

deflate圧縮コーデックを作成します。

## 引数

  * `level`: 圧縮レベル (-1..9)
  * `windowbits`: 履歴バッファのサイズ (8..15)
  * `memlevel`: 内部圧縮状態に使用されるメモリサイズ (1..9)
  * `strategy`: 圧縮戦略

      * 0 <-> Z*DEFAULT*STRATEGY
      * 1 <-> Z_FILTERED
      * 2 <-> Z*HUFFMAN*ONLY
      * 3 <-> Z_RLE
      * 4 <-> Z_FIXED
