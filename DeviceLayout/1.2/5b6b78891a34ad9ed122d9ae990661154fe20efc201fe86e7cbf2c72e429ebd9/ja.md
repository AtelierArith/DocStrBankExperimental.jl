```
function map_metadata!(geom::GeometryStructure, map_meta)
```

`geom`の各要素に対して、元のメタデータ`m`を持つものについて、そのメタデータを`map_meta(m)`に設定します。

参照された構造体に対して再帰的に行います。
