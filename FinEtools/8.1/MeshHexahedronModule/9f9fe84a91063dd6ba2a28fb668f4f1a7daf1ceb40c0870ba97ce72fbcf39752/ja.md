```
H8extrudeQ4(
    fens::FENodeSet,
    fes::FESetQ4,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

四角形のメッシュを八面体（H8）のメッシュに押し出します。
