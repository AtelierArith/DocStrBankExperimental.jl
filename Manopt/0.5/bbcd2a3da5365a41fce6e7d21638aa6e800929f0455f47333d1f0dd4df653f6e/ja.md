```
primal_residual(p, o, x_old, X_old, n_old)
```

現在の反復 $k$ におけるプライマル残差を、前の反復からの必要な値 $x_{k-1}, X_{k-1}$、および $n_{k-1}$ を用いて計算します。

$$
\Bigl\lVert
\frac{1}{σ}\operatorname{retr}^{-1}_{x_{k}}x_{k-1} -
V_{x_k\gets m_k}\bigl(DΛ^*(m_k)\bigl[V_{n_k\gets n_{k-1}}X_{k-1} - X_k \bigr]
\Bigr\rVert
$$

ここで、$V_{⋅\gets⋅}$ は [`ChambollePockState`](@ref) で使用されるベクトル輸送です。
