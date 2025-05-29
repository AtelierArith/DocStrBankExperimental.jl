```
TileData{T}
```

`MeshArray` 構造体または `BinData` 構造体（`vals` を参照）を含むデータ構造で、タイルレイアウトを説明する `MeshArray` 構造体（`tileinfo`）や、タイルデータの読み書きに関するその他の情報を含みます。

```
struct TileData{T}
    vals::T
    tileinfo::Dict
    tilesize::Tuple
    precision::Type
    numtiles::Int
end
```
