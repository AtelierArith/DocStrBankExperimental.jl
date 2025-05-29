```
AlgebraicWeight{T<:Real} <: Weight
```

与えられた `rate` に関連する代数的重みで、`isfinite(rate) & (rate ≥ 0)` を満たします。

フィールド:

  * `rate :: T`

参照: [`algebraicweight`](@ref), [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref) および [`BesselWeight`](@ref).

# 例

```jldoctest
julia> w = AlgebraicWeight(1.0)
AlgebraicWeight(1.0)

julia> rate(w)
1.0
```
