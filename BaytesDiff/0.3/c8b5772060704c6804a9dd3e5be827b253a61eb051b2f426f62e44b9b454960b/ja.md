```julia
struct AnalyticalDiffTune{G<:Function, H<:Union{Nothing, Function}} <: BaytesDiff.AbstractDifferentiableTune
```

目的関数の評価と勾配を取るための情報を格納します。

# フィールド

  * `gradient::Function`: 制約のない空間におけるℓobjectiveとパラメータベクトルの関数としての勾配、gradient(ℓobjective, θᵤ)。
  * `hessian::Union{Nothing, Function}`: 制約のない空間におけるℓobjectiveとパラメータベクトルの関数としてのヘッセ行列、hessian(ℓobjective, θᵤ)。
