```
OneSampleADTestPooled(ud::UncertainDataset, d::UnivariateDistribution,
    n::Int = 1000)) -> OneSampleADTest
```

まず、`ud`の各不確実な値の`n`回の実現を描き、それらを一緒にプールします。次に、プールされた値が分布`d`から来ているという帰無仮説に対して、サンプルが`d`から抽出されていないという対立仮説の下で、1標本アンダーソン–ダーリング検定を実施します。
