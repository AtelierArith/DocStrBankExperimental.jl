```
gevfit(y,
    locationcov = Vector{Variable}(),
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}()
    )
```

GEVパラメータを推定します。

# 引数

  * `y::Vector{<:Real}`: ブロック最大値のベクター。
  * `locationcov::Vector{<:DataItem} = Vector{Variable}()`: 位置パラメータの共変量。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: 対数スケールパラメータの共変量。
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: 形状パラメータの共変量。
