```
MatrixFactorization(
    data::DataAccessor,
    n_factors::Integer
)
```

Recommendation based on matrix factorization (MF). Number of factors $k$ is configured by `n_factors`.

MF solves the following minimization problem for a set of observed user-item interactions $\mathcal{S} = \{(u, i) \in \mathcal{U} \times \mathcal{I}\}$:

$$
\min_{P, Q} \sum_{(u, i) \in \mathcal{S}} \left( r_{u,i} - \mathbf{p}_u^{\mathrm{T}} \mathbf{q}_i \right)^2 + \lambda \ (\|\mathbf{p}_u\|^2 + \|\mathbf{q}_i\|^2),
$$

where $\mathbf{p}_u, \mathbf{q}_i \in \mathbb{R}^k$ are respectively a factorized user and item vector, and $\lambda$ is a regularization parameter to avoid overfitting. An optimal solution will be found by stochastic gradient descent (SGD). Ultimately, we can predict missing values in $R$ by just computing $PQ^{\mathrm{T}}$, and the prediction directly leads recommendation.
