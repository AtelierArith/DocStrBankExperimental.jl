```
DGMultiMesh(dg::DGMulti{NDIMS}, vertex_coordinates, EToV;
            is_on_boundary=nothing,
            periodicity=ntuple(_->false, NDIMS)) where {NDIMS}
```

  * `dg::DGMulti` contains information associated with to the reference element (e.g., quadrature, basis evaluation, differentiation, etc).
  * `vertex_coordinates` is a tuple of vectors containing x,y,... components of the vertex coordinates
  * `EToV` is a 2D array containing element-to-vertex connectivities for each element
  * `is_on_boundary` specifies boundary using a `Dict{Symbol, <:Function}`
  * `periodicity` is a tuple of booleans specifying if the domain is periodic `true`/`false` in the (x,y,z) direction.
