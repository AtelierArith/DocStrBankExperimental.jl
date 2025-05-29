```
mismatch_expression(sim::AbstractVector{<:Real}, metric::AbstractMetric, X::Vector{VariableRef}, X_len::Int) -> QuadExpr
```

## 引数

  * `sim::AbstractVector{<:Real}`: シミュレーションデータのベクトル。
  * `metric::AbstractMetric`: メトリック記述子のインスタンス（例: `MeanMetric`, `CategoryMetric` など）。
  * `X::Vector{VariableRef}`: JuMP変数参照のベクトル。
  * `X_len::Int`: JuMP変数参照のベクトルの長さ。

シミュレーションデータ `sim` とターゲットメトリック `metric` の不一致を定量化する式を返します。具体的な式は `AbstractMetric` のサブタイプに依存します。
