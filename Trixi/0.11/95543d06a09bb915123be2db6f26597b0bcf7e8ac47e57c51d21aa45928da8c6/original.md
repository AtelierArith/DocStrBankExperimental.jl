```
DGMultiMesh(dg::DGMulti{NDIMS}, cells_per_dimension, mapping;
            is_on_boundary=nothing,
            periodicity=ntuple(_ -> false, NDIMS), kwargs...) where {NDIMS}
```

Constructs a `Curved()` [`DGMultiMesh`](@ref) with element type `dg.basis.element_type`.

  * `mapping` is a function which maps from a reference [-1, 1]^NDIMS domain to a mapped domain,  e.g., `xy = mapping(x, y)` in 2D.
  * `is_on_boundary` specifies boundary using a `Dict{Symbol, <:Function}`
  * `periodicity` is a tuple of `Bool`s specifying periodicity = `true`/`false` in the (x,y,z) direction.
