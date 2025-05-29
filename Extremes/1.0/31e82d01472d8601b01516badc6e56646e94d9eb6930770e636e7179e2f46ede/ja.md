```
gumbelfit(df::DataFrame,
    datacol::Symbol,
    locationcovid = Vector{Symbol}(),
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}()
    )
```

Gumbelパラメータを推定します。

# 引数

  * `df::DataFrame`: データを含むデータフレーム。
  * `datacol::Symbol`: `df`のブロックマキシマデータを含む列のシンボル。
  * `locationcovid::Vector{Symbol} = Vector{Symbol}()`: ロケーションパラメータの共変量を含む`df`の列のシンボル。
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: ログスケールパラメータの共変量を含む`df`の列のシンボル。
