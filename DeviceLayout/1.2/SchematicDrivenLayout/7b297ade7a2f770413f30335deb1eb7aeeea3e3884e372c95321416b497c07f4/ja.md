```
function map_metadata(comp::AbstractComponent, map_meta)
```

`geometry(comp)` の各要素に対して、元のメタ `m` を持つもののメタデータを `map_meta(m)` に設定します。

参照された構造体に対して再帰的に行います。
