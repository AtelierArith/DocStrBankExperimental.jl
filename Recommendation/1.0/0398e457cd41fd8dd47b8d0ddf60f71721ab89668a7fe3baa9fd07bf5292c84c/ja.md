```
FactorizationMachines(
    data::DataAccessor,
    n_factors::Integer
)
```

第二次の因子分解機械（FM）に基づく推薦。因子の数 $k$ は `n_factors` によって設定されます。

FMの学習にはパラメータのセット $\Theta = \{w_0, \mathbf{w}, V\}$ と損失関数 $\ell(\hat{y}(\mathbf{x} \mid \Theta), y)$ が必要です。最終的に、パラメータは確率的勾配降下法（SGD）によって最適化できます。
