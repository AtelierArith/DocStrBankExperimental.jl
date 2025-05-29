```
quantileregression(X, y, tau = 0.5)
```

与えられた回帰設定に対して、分位点回帰推定量を使用して線形回帰のパラメータを推定します。

# 引数

  * `X::AbstractMatrix{Float64}`: 線形モデルのデザイン行列。
  * `y::AbstractVector{Float64}`: 線形モデルの応答ベクトル。
  * `tau::Float64`: 分位点レベル。デフォルトは0.5です。

# 例

```julia-repl
julia> income = [420.157651, 541.411707, 901.157457, 639.080229, 750.875606];
julia> foodexp = [255.839425, 310.958667, 485.680014, 402.997356, 495.560775];

julia> n = length(income)
julia> X = hcat(ones(Float64, n), income)

julia> result = quantileregression(X, foodexp, tau = 0.25)
```
