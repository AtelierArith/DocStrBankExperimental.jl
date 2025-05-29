```
BDAAutocovMethod <: AbstractAutocovMethod
```

`BDAAutocovMethod`は、MCMCチェーンの平均自己共分散を推定するための標準アルゴリズムを使用します。

これは、[^VehtariGelman2021]による議論に基づいており、[^BDA3]で議論されている自己相関関数の変動推定器を使用しています。

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)

[^BDA3]: Gelman, A., Carlin, J. B., Stern, H. S., Dunson, D. B., Vehtari, A., & Rubin, D. B. (2013). Bayesian data analysis. CRC press.
