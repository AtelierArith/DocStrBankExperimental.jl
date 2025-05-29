```
GeometricWeight{T<:Real} <: Weight
```

与えられた `rate` に関連する幾何学的重みで、`isfinite(rate) & (rate ≥ 1)` を満たします。

フィールド:

  * `rate :: T`

参照: [`geometricweight`](@ref), [`IdentityWeight`](@ref), [`AlgebraicWeight`](@ref), [`algebraicweight`](@ref) および [`BesselWeight`](@ref).

# 例

```jldoctest
julia> w = GeometricWeight(1.0)
GeometricWeight(1.0)

julia> rate(w)
1.0
```
