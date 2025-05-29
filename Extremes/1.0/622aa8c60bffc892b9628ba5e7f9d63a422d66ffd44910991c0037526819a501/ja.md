```
gevfitbayes(y,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}(),
    niter::Int=5000,
    warmup::Int=2000
    )
```

GEVパラメータの事後分布からサンプルを生成します。

# 引数

  * `y::Vector{<:Real}`: ブロック最大値のベクトル。
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: 位置パラメータの共変量。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: 対数スケールパラメータの共変量。
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: 形状パラメータの共変量。
