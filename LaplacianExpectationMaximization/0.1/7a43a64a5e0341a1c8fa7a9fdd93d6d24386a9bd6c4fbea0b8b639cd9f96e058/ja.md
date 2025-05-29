```
mc_marginal_logp(data, model::PopulationModel, params;
                 repetitions = 20, n_samples = 10^4, rng = Random.default_rng())
```

モデルに基づいてデータの周辺対数確率を推定するために、母集団からサンプリングします。
