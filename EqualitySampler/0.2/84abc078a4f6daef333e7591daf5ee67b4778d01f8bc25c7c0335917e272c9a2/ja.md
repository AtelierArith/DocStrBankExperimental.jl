```
prediction_rule(d::AbstractPartitionDistribution, r::Integer)
prediction_rule(d::Type{<:AbstractPartitionDistribution}, r::Integer, args...)
```

パーティション分布の予測ルールを計算します。すなわち、新しい観測が新しい（未見の）クラスターに属する確率です。現在のクラスターの数は `r` で示されます。
