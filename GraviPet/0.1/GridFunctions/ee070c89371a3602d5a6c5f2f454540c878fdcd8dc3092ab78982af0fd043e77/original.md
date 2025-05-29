```
GridFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
GridFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
```

Create a zero-valued grid function, i.e. a grid function that is zero everywhere. The `codomain` can be a zero-valued domain created via [`Box{DT,T}()`](@ref).

`grid_size` specifies the resolution of the grid function. This makes it convenient to use zero-valued grid functions as "templates" or "skeletons" when creating other grid functions.

This zero-valued grid function is represented efficiently and does *not* store one element per grid point.
