```
InverseVarianceWeights <: ComputedWeights
```

逆ノイズ分散重み付け、すなわち `w[l] = 1/v[l]`。

# コンストラクタ

  * `InverseVarianceWeights(v=noisevar)` 既知のノイズ分散 `noisevar` のため
  * `InverseVarianceWeights()` 未知のノイズ分散のため；ノイズ分散はデータから推定されます
