```
dual_residual(p, o, x_old, X_old, n_old)
```

現在の反復 $k$ における双対残差を、前の反復からの必要な値 $x_{k-1}, X_{k-1}$、および $n_{k-1}$ を用いて計算します。式は使用される `o.variant` によってわずかに異なります。

`：linearized` の場合は次のようになります。

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

`：exact` バリアントの場合は次のようになります。

$$
\Bigl\lVert
\frac{1}{τ} V_{n_{k}\gets n_{k-1}}(X_{k-1})
-
\operatorname{retr}^{-1}_{n_{k}}\bigl(
Λ(\operatorname{retr}_{m_{k}}(V_{m_k\gets x_k}\operatorname{retr}^{-1}_{x_{k}}x_{k-1}))
\bigr)
\Bigr\rVert
$$

ここで、両方のケースにおいて $V_{⋅\gets⋅}$ は [`ChambollePockState`](@ref) で使用されるベクトル輸送です。
