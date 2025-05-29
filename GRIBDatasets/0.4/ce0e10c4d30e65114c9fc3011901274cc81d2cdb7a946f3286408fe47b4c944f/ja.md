```
FileIndex(grib_path::String; index_keys = ALL_KEYS, filter_by_values = Dict())
```

ファイル `grib_path` のための [`FileIndex`](@ref) を構築し、`index_keys` にあるキーのみを保存します。`filter_by_values` で指定することにより、特定の値のみを読み取ることが可能です。ヘッダーの値には `getindex` を使用してアクセスできます。
