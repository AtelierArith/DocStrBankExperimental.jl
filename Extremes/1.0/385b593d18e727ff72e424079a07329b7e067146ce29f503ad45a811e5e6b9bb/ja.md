```
gpfit(y,
    logscalecov = Vector{Variable}(),
    shapecov = Vector{Variable}()
    )
```

GPパラメータを推定します

# 引数

  * `y::Vector{<:Real}`: 超過のベクトル。
  * `logscalecov::Vector{<:DataItem} = Vector{Variable}()`: 対数スケールパラメータの共変量。
  * `shapecov::Vector{<:DataItem} = Vector{Variable}()`: 形状パラメータの共変量。
