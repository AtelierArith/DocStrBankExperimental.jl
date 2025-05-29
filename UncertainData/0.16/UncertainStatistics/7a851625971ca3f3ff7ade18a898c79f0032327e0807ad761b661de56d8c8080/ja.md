```
OneSampleADTest(uv::UncertainValue, d::UnivariateDistribution,
    n::Int = 1000) -> OneSampleADTest
```

不確実な値 `uv` の `n` 回の実現が分布 `d` からのものであるという帰無仮説に対して、サンプルが `d` から抽出されていないという対立仮説のもとで、1標本アンダーソン–ダーリング検定を実行します。
