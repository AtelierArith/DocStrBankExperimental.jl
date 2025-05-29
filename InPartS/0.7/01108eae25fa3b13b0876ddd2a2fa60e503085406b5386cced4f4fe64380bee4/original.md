```
Domain3D{BCX, BCY, BCZ}(size::SVector{3, Float64})
Domain3D{BCX, BCY, BCZ}(w, h, d)
Domain3D(args; [boundaries = (BCX, BCY, BCZ)])
```

Create a three-dimensional cuboid domain of dimensions `SA[w, h, d]`

`Domain3D`s are parametrized by three [`Boundary`](@ref) types that represent the boundary conditions in the three dimensions.

See also: [`Domain2D`]
