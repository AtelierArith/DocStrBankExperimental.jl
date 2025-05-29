```
BesselWeight{T<:Real} <: Weight
```

Bessel weight associated with a given `rate` satisfying `isfinite(rate) & (rate ≥ 0)`.

Field:

  * `rate :: T`

See also: [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref), [`AlgebraicWeight`](@ref) and [`algebraicweight`](@ref).

# Examples

```jldoctest
julia> w = BesselWeight(1.0)
BesselWeight(1.0)

julia> rate(w)
1.0
```
