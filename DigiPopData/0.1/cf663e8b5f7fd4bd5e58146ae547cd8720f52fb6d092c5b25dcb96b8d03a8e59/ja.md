```
mismatch(sim::AbstractVector{<:Real}, metric::AbstractMetric) -> Float64
```

## 引数

  * `sim::AbstractVector{<:Real}`: シミュレーションデータのベクトル。
  * `metric::AbstractMetric`: メトリック記述子のインスタンス（例: `MeanMetric`, `CategoryMetric` など）。

シミュレーションデータ `sim` とターゲットメトリック `metric` の不一致を定量化する損失を返します。具体的な式は `AbstractMetric` のサブタイプによって異なります。
