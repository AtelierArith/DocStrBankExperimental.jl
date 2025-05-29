```
Domain2D{BCX, BCY, BCZ}(size::SVector{2, Float64})
Domain2D{BCX, BCY, BCZ}(w, h)
Domain2D(args; [boundaries = (BCX, BCY, BCZ)])
```

Create a two-dimensional rectangular domain of dimensions `SA[w, h]`

`Domain2D`s are parametrized by two [`Boundary`](@ref) types that represent the boundary conditions in the two dimensions.

See also: [`Domain3D`]
