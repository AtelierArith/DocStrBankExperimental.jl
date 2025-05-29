```
gaussian_gapprox(prior::AbstractSimulatorPrior; num_prior_samples::Int=10_000, rng::Random.AbstractRNG=Random.default_rng())
```

与えられた `prior` 分布の経験的多変量ガウス近似を構築するために、変換されたサンプルのモーメントを計算します。
