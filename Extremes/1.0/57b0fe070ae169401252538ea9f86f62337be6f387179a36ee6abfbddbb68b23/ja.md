```
gpfitbayes(y,
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}(),
    niter::Int=5000,
    warmup::Int=2000
    )
```

GPパラメータの事後分布からサンプルを生成します。

# 引数

  * `y::Vector{<:Real}`: 超過のベクトル。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: 対数スケールパラメータの共変量。
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: 形状パラメータの共変量。
