```
project(M::CenteredMatrices, p)
```

Projects `p` from the embedding onto the [`CenteredMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_{\mathcal M}(p) = p - \begin{bmatrix}
1\\
⋮\\
1
\end{bmatrix} * [c_1 \dots c_n],
$$

where $c_i = \frac{1}{m}\sum_{j=1}^m p_{j,i}$ for $i = 1, \dots, n$.
