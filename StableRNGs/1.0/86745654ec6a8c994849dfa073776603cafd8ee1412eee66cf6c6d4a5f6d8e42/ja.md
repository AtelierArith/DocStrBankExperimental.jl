```
LehmerRNG
StableRNG
```

安定したストリームを持つシンプルなRNGで、通常はテストに適しています。名前 `LehmerRNG` はAPIの一部ではないため、エイリアス `StableRNG` のみを使用してください。

構築: `StableRNG(seed::Integer)`。

シード設定: `Random.seed!(rng::StableRNG, seed::Integer)`。
