```
initrbm(x, nhidden)
initrbm(x, nhidden, rbmtype)
```

`nhidden` 隠れユニットを持つ RBM を作成し、データセット `x` のトレーニングのためにその重みを初期化します。`rbmtype` は `AbstractRBM` のサブタイプであり、デフォルトは `BernoulliRBM` です。
