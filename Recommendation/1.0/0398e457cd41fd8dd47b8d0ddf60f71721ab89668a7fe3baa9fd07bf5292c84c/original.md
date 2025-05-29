```
FactorizationMachines(
    data::DataAccessor,
    n_factors::Integer
)
```

Recommendation based on second-order factorization machines (FMs). Number of factors $k$ is configured by `n_factors`.

Learning FM requires a set of parameters $\Theta = \{w_0, \mathbf{w}, V\}$ and a loss function $\ell(\hat{y}(\mathbf{x} \mid \Theta), y)$. Ultimately, the parameters can be optimized by stochastic gradient descent (SGD).
