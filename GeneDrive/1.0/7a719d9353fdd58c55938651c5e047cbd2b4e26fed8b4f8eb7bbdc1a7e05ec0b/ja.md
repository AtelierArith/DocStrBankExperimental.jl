```
mutable struct TemperatureSeriesData <: ExogenousChange
    node::Symbol
    times::Vector{Float64}
    values::Vector{Float64}
    set::diffeq.CallbackSet
end
```

温度の時系列データ。

# 引数

  * `node::Symbol`: 温度が実現される`Node`。
  * `times::Vector{Float64}`: 実現された温度値の時間ステップ（日）。
  * `values::Vector{Float64}`: 温度（°C）。
  * `set::diffeq.CallbackSet`
