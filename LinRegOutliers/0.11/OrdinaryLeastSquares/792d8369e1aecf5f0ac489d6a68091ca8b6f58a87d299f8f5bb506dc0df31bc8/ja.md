```
wls(X, y, wts)

加重最小二乗回帰を推定し、推定されたパラメータを持つOLSオブジェクトを作成します。
```

# 引数

  * `X::AbstractMatrix{Float64}`: デザイン行列。
  * `y::AbstractVector{Float64}`: 応答ベクトル。
  * `wts::AbstractVector{Float64}`: 重みベクトル。

# 例

```julia-repl
julia> X = hcat(ones(24), phones[:,"year"]);
julia> y = phones[:,"calls"];
julia> w = ones(24)
julia> w[15:20] .= 0.0
julia> reg = wls(X, y, w)
julia> reg.betas
2-element Vector{Float64}:
 -63.481644325290425
   1.3040571939231453
```
