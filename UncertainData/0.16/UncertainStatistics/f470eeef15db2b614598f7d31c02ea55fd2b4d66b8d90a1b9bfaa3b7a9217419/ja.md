```
ExactOneSampleKSTestElementWise(ud::UncertainDataset,
    d::UnivariateDistribution, n::Int = 1000) -> Vector{ExactOneSampleKSTest}
```

まず、`ud`内の各不確実な値の`n`回の実現を引き出し、各不確実な値のために1つの値のプールを保持します。

次に、各値のプールが分布`d`から来ているという帰無仮説に対して、サンプルが`d`から引き出されていないという対立仮説のもとで、要素ごとの（プールごとの）1サンプルの正確なコルモゴロフ–スミルノフ検定を実施します。
