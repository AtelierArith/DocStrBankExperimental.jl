```
project(M::CenteredMatrices, p, X)
```

Project the matrix `X` onto the tangent space at `p` on the [`CenteredMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_p(X) = X - \begin{bmatrix}
1\\
⋮\\
1
\end{bmatrix} * [c_1 \dots c_n],
$$

where $c_i = \frac{1}{m}\sum_{j=1}^m x_{j,i}$  for $i = 1, \dots, n$.
