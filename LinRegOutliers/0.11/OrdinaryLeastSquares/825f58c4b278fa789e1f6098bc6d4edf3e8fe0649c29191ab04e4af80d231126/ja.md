```
ols(X, y)

推定された回帰係数を持つOLSオブジェクトを作成します。
```

# 引数

  * `X::AbstractMatrix{Float64}`: デザイン行列。
  * `y::AbstractVector{Float64}`: 応答ベクトル。

# 例

```julia-repl
julia> X = hcat(ones(24), phones[:,"year"]);
julia> y = phones[:,"calls"];
julia> reg = ols(X, y)
julia> reg.betas
2-element Vector{Float64}:
 -260.0592463768119
    5.04147826086957
```
