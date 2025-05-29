```
dual_residual(p, o, x_old, X_old, n_old)
```

Compute the dual residual at current iterate $k$ given the necessary values $x_{k-1}, X_{k-1}$, and $n_{k-1}$ from the previous iterate. The formula is slightly different depending on the `o.variant` used:

For the `:linearized` it reads

$$
\Bigl\lVert
\frac{1}{τ}\bigl(
V_{n_{k}\gets n_{k-1}}(X_{k-1})
- X_k
\bigr)
-
DΛ(m_k)\bigl[
V_{m_k\gets x_k}\operatorname{retr}^{-1}_{x_{k}}x_{k-1}
\bigr]
\Bigr\rVert
$$

and for the `:exact` variant

$$
\Bigl\lVert
\frac{1}{τ} V_{n_{k}\gets n_{k-1}}(X_{k-1})
-
\operatorname{retr}^{-1}_{n_{k}}\bigl(
Λ(\operatorname{retr}_{m_{k}}(V_{m_k\gets x_k}\operatorname{retr}^{-1}_{x_{k}}x_{k-1}))
\bigr)
\Bigr\rVert
$$

where in both cases $V_{⋅\gets⋅}$ is the vector transport used in the [`ChambollePockState`](@ref).
