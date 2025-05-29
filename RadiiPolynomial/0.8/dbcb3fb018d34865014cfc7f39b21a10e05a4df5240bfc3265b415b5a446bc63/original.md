```
AlgebraicWeight{T<:Real} <: Weight
```

Algebraic weight associated with a given `rate` satisfying `isfinite(rate) & (rate ≥ 0)`.

Field:

  * `rate :: T`

See also: [`algebraicweight`](@ref), [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref) and [`BesselWeight`](@ref).

# Examples

```jldoctest
julia> w = AlgebraicWeight(1.0)
AlgebraicWeight(1.0)

julia> rate(w)
1.0
```
