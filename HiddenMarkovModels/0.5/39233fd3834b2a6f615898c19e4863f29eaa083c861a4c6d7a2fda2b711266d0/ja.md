```
obs_distributions(hmm)
obs_distributions(hmm, control)
```

`hmm`の各状態に対する観測分布のベクトルを返します（`control`が適用される場合もあります）。

これらの分布オブジェクトは以下を実装する必要があります。

  * `Random.rand(rng, dist)`によるサンプリング
  * `DensityInterface.logdensityof(dist, obs)`による推論
  * `StatsAPI.fit!(dist, obs_seq, weight_seq)`による学習
