```
DimKeys <: AbstractArray

DimKeys(x)
DimKeys(dims::Tuple)
DimKeys(dims::Dimension)
```

`CartesianIndices`のように、しかしDimensionsのルックアップ値のためのものです。`dims`のルックアップ値のすべての組み合わせに対して、`Dimension(At(lookupvalue))`の`Tuple`の`Array`として振る舞います。
