```
enable!(sampler, clock, distribution, enablingtime, currenttime, RNG)
```

サンプラーにクロックを開始するよう指示します。

  * `sampler::SSA{KeyType,TimeType}` - 指示するサンプラー。
  * `clock::KeyType` - クロックのID。文字列、整数、タプルなどが可能です。
  * `distribution::Distributions.UnivariateDistribution`
  * `enablingtime::TimeType` - クロックの分布のゼロ時間、絶対時間で。通常は `when` と等しいです。
  * `when::TimeType` - シミュレーションの現在の時間。
  * `rng::AbstractRNG` - 擬似乱数生成器。
