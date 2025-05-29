```
mutable struct TemperatureShockData <: ExogenousChange
    node::Symbol
    times::Vector{Tuple{Float64, Float64}}
    values::Union{Float64, Vector{Float64}}
    set::diffeq.CallbackSet
end
```

温度ショックのデータ。

# 引数

  * `node::Symbol`: 温度ショックが発生する`Node`。
  * `times::Vector{Tuple{Float64,Float64}}`: ショックの開始/停止時間ポイントを定義するタプルのベクター。複数の離散的なショック期間を含めることができます。
  * `values::Union{Float64, Vector{Float64}}`: 指定された時間期間中に基準温度に加えられる°Cの単一の固定温度値または°Cの変動温度値のベクター。複数の離散的な温度変化を含めることができ、値は正または負である可能性があります。
  * `set::diffeq.CallbackSet`
