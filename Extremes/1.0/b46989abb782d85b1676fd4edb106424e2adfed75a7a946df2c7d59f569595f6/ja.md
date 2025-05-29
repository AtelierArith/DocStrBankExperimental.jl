```
gpfit(df::DataFrame,
    datacol::Symbol,
    logscalecovid = Vector{Symbol}(),
    shapecovid = Vector{Symbol}()
    )
```

GPパラメータを推定します

# 引数

  * `df::DataFrame`: データを含むデータフレーム。
  * `datacol::Symbol`: 超過値を含む`df`の列のシンボル。
  * `initialvalues::Vector{<:Real}`: パラメータの初期値のベクトル。
  * `logscalecovid::Vector{Symbol} = Vector{Symbol}()`: ログスケールパラメータの共変量を含む`df`の列のシンボルのベクトル。
  * `shapecovid::Vector{Symbol} = Vector{Symbol}()`: 形状パラメータの共変量を含む`df`の列のシンボルのベクトル。
