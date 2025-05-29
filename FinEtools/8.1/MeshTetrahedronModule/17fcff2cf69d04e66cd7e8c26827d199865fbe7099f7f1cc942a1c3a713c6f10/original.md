```
T4extrudeT3(
    fens::FENodeSet,
    fes::FESetT3,
    nLayers::IT,
    extrusionh::F,
) where {F<:Function, IT<:Integer}
```

Extrude a mesh of triangles into a mesh of tetrahedra (T4).
