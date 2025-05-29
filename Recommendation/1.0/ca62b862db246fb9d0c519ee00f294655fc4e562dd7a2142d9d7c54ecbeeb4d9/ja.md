```
BPRMatrixFactorization(
    data::DataAccessor,
    n_factors::Integer
)
```

行列因子分解（MF）に基づく推薦で、ベイジアン個人化ランキング（BPR）損失を使用します。因子の数 $k$ は `n_factors` で設定されます。

  * [BPR: Bayesian Personalized Ranking from Implicit Feedback](https://dl.acm.org/doi/10.5555/1795114.1795167)
