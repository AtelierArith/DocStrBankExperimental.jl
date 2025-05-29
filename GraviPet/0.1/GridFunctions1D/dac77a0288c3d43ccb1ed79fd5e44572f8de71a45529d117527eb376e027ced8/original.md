```
GridFunction1D{S,T}(name::AbstractString, domain::Interval{S}, codomain::Interval{T}, npoints::Int)
GridFunction1D(name::AbstractString, domain::Interval{S}, codomain::Interval{T}, npoints::Int)
```

Create a zero-valued grid function, i.e. a grid function that is zero everywhere. The `codomain` can be a zero-valued domain created via [`Interval{T}()`](@ref).

`npoints` specifies the resolution of the grid function. This makes it convenient to use zero-valued grid functions as "templates" or "skeletons" when creating other grid functions.

This zero-valued grid function is represented efficiently and does *not* store one element per grid point.
