```
DGMultiMesh(dg::DGMulti, cells_per_dimension;
            coordinates_min=(-1.0, -1.0), coordinates_max=(1.0, 1.0),
            is_on_boundary=nothing,
            periodicity=ntuple(_ -> false, NDIMS))
```

Constructs a Cartesian [`DGMultiMesh`](@ref) with element type `dg.basis.element_type`. The domain is the tensor product of the intervals `[coordinates_min[i], coordinates_max[i]]`.

  * `is_on_boundary` specifies boundary using a `Dict{Symbol, <:Function}`
  * `periodicity` is a tuple of `Bool`s specifying periodicity = `true`/`false` in the (x,y,z) direction.
