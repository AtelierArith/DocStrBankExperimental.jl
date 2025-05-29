```
gpfitbayes(df::DataFrame,
    datacol::Symbol,
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}(),
    niter::Int=5000,
    warmup::Int=2000)
```

GPパラメータの事後分布からサンプルを生成します。

# 引数

  * `df::DataFrame`: データを含むデータフレーム。
  * `datacol::Symbol`: `df`の超過を含む列のシンボル。
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: ログスケールパラメータの共変量を含む`df`の列のシンボル。
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: 形状パラメータの共変量を含む`df`の列のシンボル。
