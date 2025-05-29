```julia
struct ℓGradientResult{T<:(AbstractVector), S<:Real, G<:(AbstractVector)} <: BaytesDiff.ℓObjectiveResult
```

'ℓobjective' 評価における 'parameter' の対数密度、勾配、およびパラメータの結果を格納します。

# フィールド

  * `θᵤ::AbstractVector`: 制約のない空間におけるパラメータ。
  * `ℓθᵤ::Real`: θᵤ における対数密度。
  * `∇ℓθᵤ::AbstractVector`: θᵤ における対数密度の勾配。
