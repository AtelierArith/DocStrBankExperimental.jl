```
SVD(
    data::DataAccessor,
    n_factors::Integer
)
```

Recommendation based on SVD of a user-item matrix $R \in \mathbb{R}^{|\mathcal{U}| \times |\mathcal{I}|}$, which was originally studied by [Sarwar et al.](http://files.grouplens.org/papers/webKDD00.pdf) Rank $k$ is configured by `n_factors`. Sparse matrix is not supported for `data.R`.

In a context of recommendation, $U_k \in \mathbb{R}^{|\mathcal{U}| \times k}$, $V \in \mathbb{R}^{|\mathcal{I}| \times k}$ and $\Sigma \in \mathbb{R}^{k \times k}$ are respectively seen as $k$ user/item feature vectors and corresponding weights. The idea of low-rank approximation that discards lower singular values intuitively works as *compression* or *denoising* of the original matrix; that is, each element in a rank-$k$ matrix $A_k$ holds the best *compressed* (or *denoised*) value of the original element in $A$. Thus, $R_k = \mathrm{SVD}_k(R)$, the best rank-$k$ approximation of $R$, captures as much as possible of underlying users' preferences. Once $R$ is decomposed into $U, \Sigma$ and $V$, a $(u, i)$ element of $R_k$ calculated by $\sum^k_{j=1} \sigma_j u_{u, j} v_{i, j}$ could be a prediction for the user-item pair.
