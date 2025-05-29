```
TileData{T}
```

Data structure containing either a `MeshArray` struct or `BinData` struct (see `vals`),     `MeshArray` structs describing the tile layout (`tileinfo`), and other information for     reading/writing tile data.

```
struct TileData{T}
    vals::T
    tileinfo::Dict
    tilesize::Tuple
    precision::Type
    numtiles::Int
end
```
