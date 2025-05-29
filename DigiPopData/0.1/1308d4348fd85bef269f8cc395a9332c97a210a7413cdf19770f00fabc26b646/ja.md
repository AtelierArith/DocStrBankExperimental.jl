```
MeanSDMetric <: AbstractMetric
```

シミュレーションされたデータセットの平均と標準偏差（SD）をターゲットの平均とSDと比較するメトリックです。

## フィールド

  * `size::Int`: データセットのサイズ。
  * `mean::Float64`: ターゲット平均値。
  * `sd::Float64`: ターゲット標準偏差値。
