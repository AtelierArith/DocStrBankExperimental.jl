```
set_points!(p::PlanNUFFT, points)
```

Set non-uniform points before executing a NUFFT.

In one dimension, `points` is simply a vector of real values (the non-uniform locations).

In multiple dimensions, `points` may be passed as:

  * a tuple of vectors `(xs::AbstractVector, ys::AbstractVector, …)` (**should be preferred**);
  * a vector `[x⃗₁, x⃗₂, x⃗₃, x⃗₄, …]` of tuples or static vectors (typically `SVector`s from the StaticArrays.jl package);
  * a matrix of size `(d, Np)` where `d` is the spatial dimension and `Np` the number of non-uniform points.

The first format should be preferred if one wants to avoid extra allocations.

For convenience (and backwards compatibility), one can also pass a `StructVector` from the StructArrays.jl package, which is equivalent to the first option above.

The points are allowed to be outside of the periodic cell $[0, 2π)^d$, in which case they will be "folded" to that domain.

!!! note "Modifying the points arrays"
    As one may expect, this package does not modify the input points, as doing this would be surprising. However, to avoid allocations and copies, it keeps a reference to the point data when performing the transforms. This means that one should **not** modify the passed arrays between a call to `set_points!` and [`exec_type1!`](@ref) or [`exec_type2!`](@ref), as this can lead to wrong results or much worse.

