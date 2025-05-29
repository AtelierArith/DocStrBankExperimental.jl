```
ExactOneSampleKSTestPooled(ud::UncertainDataset,
    d::UnivariateDistribution, n::Int = 1000) -> ExactOneSampleKSTest
```

まず、`ud`の各不確実な値の`n`回の実現を描き、それらを一緒にプールします。次に、プールされた値が分布`d`から来ているという帰無仮説に対して、サンプルが`d`から抽出されていないという対立仮説のもとで、一標本の正確なコルモゴロフ–スミルノフ検定を実施します。
