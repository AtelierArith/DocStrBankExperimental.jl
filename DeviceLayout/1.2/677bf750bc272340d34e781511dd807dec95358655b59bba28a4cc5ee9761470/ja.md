```
function map_metadata(geom::GeometryStructure, map_meta)
```

`geom`のコピーを作成し、すべての要素に対して元のメタデータ`m`を`map_meta(m)`に変更します。

参照された構造体のコピーに対して再帰的に行います。
