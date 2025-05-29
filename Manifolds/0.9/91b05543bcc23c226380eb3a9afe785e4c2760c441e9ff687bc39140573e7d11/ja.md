```
project(M::CenteredMatrices, p)
```

埋め込みから[`CenteredMatrices`](@ref) `M`への`p`の射影、すなわち

$$
\operatorname{proj}_{\mathcal M}(p) = p - \begin{bmatrix}
1\\
⋮\\
1
\end{bmatrix} * [c_1 \dots c_n],
$$

ここで$c_i = \frac{1}{m}\sum_{j=1}^m p_{j,i}$、$i = 1, \dots, n$です。
