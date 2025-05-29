```
H8extrudeQ4(
    fens::FENodeSet,
    fes::FESetQ4,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

Extrude a mesh of quadrilaterals into a mesh of hexahedra (H8).
