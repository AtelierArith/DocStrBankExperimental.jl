```
AbstractAffineMap{N, S<:LazySet{N}} <: LazySet{N}
```

Abstract type for affine maps.

### Notes

See [`AffineMap`](@ref) for a standard implementation of this interface.

Every concrete `AbstractAffineMap` must define the following methods:

  * `matrix(::AbstractAffineMap)` – return the linear map
  * `vector(::AbstractAffineMap)` – return the affine translation vector
  * `set(::AbstractAffineMap)` – return the set that the map is applied to

The subtypes of `AbstractAffineMap`:

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractAffineMap)
7-element Vector{Any}:
 AffineMap
 ExponentialMap
 ExponentialProjectionMap
 InverseLinearMap
 LinearMap
 ResetMap
 Translation
```
