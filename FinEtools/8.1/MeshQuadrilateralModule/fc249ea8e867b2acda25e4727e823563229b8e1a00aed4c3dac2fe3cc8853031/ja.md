```
Q4extrudeL2(
    fens::FENodeSet,
    fes::FESetL2,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

線形セグメントのメッシュを四角形メッシュ（Q4）に押し出します。
