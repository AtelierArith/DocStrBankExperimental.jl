```
AbstractHyperrectangle{N} <: AbstractZonotope{N}
```

Abstract type for hyperrectangular sets.

### Notes

See [`Hyperrectangle`](@ref) for a standard implementation of this interface.

Every concrete `AbstractHyperrectangle` must define the following functions:

  * `radius_hyperrectangle(::AbstractHyperrectangle)` – return the   hyperrectangle's radius, which is a full-dimensional vector

Among other functions, the following functions are then automatically defined:

  * `isflat(::AbstractHyperrectangle)` – check whether the hyperrectangle's   radius is zero in some dimension
  * `radius_hyperrectangle(::AbstractHyperrectangle, i::Int)` – return the   hyperrectangle's radius in the `i`-th dimension

Every hyperrectangular set is also a zonotopic set; see [`AbstractZonotope`](@ref).

The subtypes of `AbstractHyperrectangle` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractHyperrectangle)
5-element Vector{Any}:
 AbstractSingleton
 BallInf
 Hyperrectangle
 Interval
 SymmetricIntervalHull
```
