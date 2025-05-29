```
storage,chunksizes = chunking(v::Variable)
```

変数 `v` のストレージタイプ（`:contiguous` または `:chunked`）とチャンクサイズを返します。
