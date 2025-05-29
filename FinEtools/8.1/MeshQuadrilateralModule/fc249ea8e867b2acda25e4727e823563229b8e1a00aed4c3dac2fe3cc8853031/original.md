```
Q4extrudeL2(
    fens::FENodeSet,
    fes::FESetL2,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

Extrude a mesh of linear segments into a mesh of quadrilaterals (Q4).
