```
DGMultiMesh(dg::DGMulti{2, Tri}, triangulateIO, boundary_dict::Dict{Symbol, Int})
```

  * `dg::DGMulti` contains information associated with to the reference element (e.g., quadrature, basis evaluation, differentiation, etc).
  * `triangulateIO` is a `TriangulateIO` mesh representation
  * `boundary_dict` is a `Dict{Symbol, Int}` which associates each integer `TriangulateIO` boundary tag with a `Symbol`.
