```
storage,chunksizes = chunking(v::Variable)
```

変数 `v` のストレージタイプ（`:contiguous` または `:chunked`）とチャンクサイズを返します。`chunking` は `nc_inq_var_chunking` と同じ情報を報告し、したがって [無制限次元を持つ変数を `:contiguous` と見なします](https://github.com/Unidata/netcdf-c/discussions/2224)。
