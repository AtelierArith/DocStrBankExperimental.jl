```
T4extrudeT3(
    fens::FENodeSet,
    fes::FESetT3,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

三角形のメッシュを四面体のメッシュ（T4）に押し出します。
