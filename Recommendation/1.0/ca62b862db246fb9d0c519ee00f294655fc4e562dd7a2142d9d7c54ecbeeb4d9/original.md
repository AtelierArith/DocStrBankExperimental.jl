```
BPRMatrixFactorization(
    data::DataAccessor,
    n_factors::Integer
)
```

Recommendation based on matrix factorization (MF) with Bayesian personalized ranking (BPR) loss. Number of factors $k$ is configured by `n_factors`.

  * [BPR: Bayesian Personalized Ranking from Implicit Feedback](https://dl.acm.org/doi/10.5555/1795114.1795167)
