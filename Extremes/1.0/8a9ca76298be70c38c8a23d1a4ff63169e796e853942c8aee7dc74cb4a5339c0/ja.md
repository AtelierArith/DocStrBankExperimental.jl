```
gumbelfitbayes(y,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}(),
    niter::Int=5000,
    warmup::Int=2000
    )
```

Gumbelパラメータの事後分布からサンプルを生成します。

# 引数

  * `y::Vector{<:Real}`: ブロック最大値のベクトル。
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: ロケーションパラメータの共変量。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: ログスケールパラメータの共変量。
