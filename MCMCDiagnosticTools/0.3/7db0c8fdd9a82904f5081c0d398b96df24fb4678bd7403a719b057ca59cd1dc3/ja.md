```
AutocovMethod <: AbstractAutocovMethod
```

`AutocovMethod`は、MCMCチェーンの平均自己共分散を推定するための標準アルゴリズムを使用します。

これは、[^VehtariGelman2021]による議論に基づいており、[^Geyer1992]で議論されているように、自己共分散のバイアス推定量を使用します。

[^VehtariGelman2021]: Vehtari, A., Gelman, A., Simpson, D., Carpenter, B., & Bürkner, P. C. (2021). Rank-normalization, folding, and localization: An improved $\widehat {R}$ for assessing convergence of MCMC. Bayesian Analysis. doi: [10.1214/20-BA1221](https://doi.org/10.1214/20-BA1221) arXiv: [1903.08008](https://arxiv.org/abs/1903.08008)

[^Geyer1992]: Geyer, C. J. (1992). Practical Markov Chain Monte Carlo. Statistical Science, 473-483.
