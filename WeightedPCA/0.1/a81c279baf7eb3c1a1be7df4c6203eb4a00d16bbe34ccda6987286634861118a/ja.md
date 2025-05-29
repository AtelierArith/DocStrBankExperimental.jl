```
OptimalWeights <: ComputedWeights
```

最適重み付け、すなわち `w[l] = 1/v[l] * 1/(1+v[l]/λ)`。

# コンストラクタ

  * `OptimalWeights(v=noisevar, λ=signalvar)` は既知のノイズ分散 `noisevar` と信号分散 `signalvar` のためのもの
  * `OptimalWeights(λ=signalvar)` は既知の信号分散 `signalvar` のためのもので、ノイズ分散はデータから推定される
  * `OptimalWeights(v=noisevar)` は既知のノイズ分散 `noisevar` のためのもので、信号分散はデータから推定される
  * `OptimalWeights()` は未知のノイズおよび信号分散のためのもので、ノイズおよび信号分散はデータから推定される
