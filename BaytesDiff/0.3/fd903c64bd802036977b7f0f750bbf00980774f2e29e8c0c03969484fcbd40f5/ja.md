```julia
struct ℓHessianResult{T<:(AbstractVector), S<:Real, G<:(AbstractVector), H<:(AbstractMatrix)} <: BaytesDiff.ℓObjectiveResult
```

'ℓobjective' 評価におけるパラメータ 'parameter' の対数密度、勾配、ヘッセ行列、およびパラメータの結果を格納します。

# フィールド

  * `θᵤ::AbstractVector`: 制約のない空間におけるパラメータ。
  * `ℓθᵤ::Real`: θᵤ における対数密度。
  * `∇ℓθᵤ::AbstractVector`: θᵤ における対数密度の勾配。
  * `Δℓθᵤ::AbstractMatrix`: θᵤ における対数密度のヘッセ行列。
