```
gevfitbayes(df::DataFrame,
    datacol::Symbol,
    locationcovid = Vector{Symbol}(),
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}(),
    niter::Int=5000,
    warmup::Int=2000)
```

GEVパラメータの事後分布からサンプルを生成します。

# 引数

  * `df::DataFrame`: データを含むデータフレーム。
  * `datacol::Symbol`: ブロックマキシマデータを含む`df`の列のシンボル。
  * `locationcovid::Vector{Symbol} = Vector{Symbol}()`: ロケーションパラメータの共変量を含む`df`の列のシンボル。
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: ログスケールパラメータの共変量を含む`df`の列のシンボル。
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: 形状パラメータの共変量を含む`df`の列のシンボル。
