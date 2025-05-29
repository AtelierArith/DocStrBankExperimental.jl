```
shrink(x)
```

Shrink an input. The returned value is a `Vector` with elements `similar` to `x`. Returning a vector of length 1 is interpreted as meaning that no further shrinkage is possible.

# Default Shrinkers

`shrink` methods for the following types are shipped with this package:

  * `AbstractString`
  * `AbstractArray{T, N}` for any `T` and `N`

# Implementation

  * Any implementation of `shrink(x::T)` must come with an implementation of [`shrinkable(x::T)`](@ref shrinkable(Any)). Failure to do so will prevent [`@quickcheck`](@ref) from calling `shrink` on an object of type `T`.
  * `shrink(x)` must return [x] if `shrinkable(x)` evaluate to `false`. We suggest that the first line of your method is something like:

```julia
shrinkable(x) || return typeof(x)[x]
```
