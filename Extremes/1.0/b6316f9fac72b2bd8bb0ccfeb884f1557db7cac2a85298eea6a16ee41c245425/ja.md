```
gevfit(df::DataFrame,
    datacol::Symbol,
    locationcovid = Vector{Symbol}(),
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}()
    )
```

GEVパラメータを推定します。

# 引数

  * `df::DataFrame`: データを含むデータフレーム。
  * `datacol::Symbol`: ブロック最大値データを含む`df`の列のシンボル。
  * `locationcovid::Vector{Symbol} = Vector{Symbol}()`: ロケーションパラメータの共変量を含む`df`の列のシンボル。
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: ログスケールパラメータの共変量を含む`df`の列のシンボル。
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: 形状パラメータの共変量を含む`df`の列のシンボル。
