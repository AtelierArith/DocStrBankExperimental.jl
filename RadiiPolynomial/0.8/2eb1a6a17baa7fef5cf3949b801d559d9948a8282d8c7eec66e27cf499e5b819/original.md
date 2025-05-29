```
GeometricWeight{T<:Real} <: Weight
```

Geometric weight associated with a given `rate` satisfying `isfinite(rate) & (rate ≥ 1)`.

Field:

  * `rate :: T`

See also: [`geometricweight`](@ref), [`IdentityWeight`](@ref), [`AlgebraicWeight`](@ref), [`algebraicweight`](@ref) and [`BesselWeight`](@ref).

# Examples

```jldoctest
julia> w = GeometricWeight(1.0)
GeometricWeight(1.0)

julia> rate(w)
1.0
```
