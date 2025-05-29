```
BesselWeight{T<:Real} <: Weight
```

与えられた `rate` に関連するベッセル重みで、`isfinite(rate) & (rate ≥ 0)` を満たします。

フィールド:

  * `rate :: T`

参照: [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref), [`AlgebraicWeight`](@ref) および [`algebraicweight`](@ref).

# 例

```jldoctest
julia> w = BesselWeight(1.0)
BesselWeight(1.0)

julia> rate(w)
1.0
```
