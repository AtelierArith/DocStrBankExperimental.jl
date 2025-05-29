```
ExactOneSampleKSTest(uv::AbstractUncertainValue,
    d::UnivariateDistribution, n::Int = 1000) -> ExactOneSampleKSTest
```

不確実な値 `uv` の `n` 回の実現が分布 `d` からのものであるという帰無仮説に対して、サンプルが `d` から抽出されていないという対立仮説のもとで、1標本の正確なコルモゴロフ–スミルノフ検定を実行します。
