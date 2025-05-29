```
project(M::CenteredMatrices, p, X)
```

行列 `X` を [`CenteredMatrices`](@ref) `M` の点 `p` での接空間に射影します。すなわち、

$$
\operatorname{proj}_p(X) = X - \begin{bmatrix}
1\\
⋮\\
1
\end{bmatrix} * [c_1 \dots c_n],
$$

ここで $c_i = \frac{1}{m}\sum_{j=1}^m x_{j,i}$ であり、$i = 1, \dots, n$ です。
