```
primal_residual(p, o, x_old, X_old, n_old)
```

Compute the primal residual at current iterate $k$ given the necessary values $x_{k-1}, X_{k-1}$, and $n_{k-1}$ from the previous iterate.

$$
\Bigl\lVert
\frac{1}{σ}\operatorname{retr}^{-1}_{x_{k}}x_{k-1} -
V_{x_k\gets m_k}\bigl(DΛ^*(m_k)\bigl[V_{n_k\gets n_{k-1}}X_{k-1} - X_k \bigr]
\Bigr\rVert
$$

where $V_{⋅\gets⋅}$ is the vector transport used in the [`ChambollePockState`](@ref)
