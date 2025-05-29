```
rotmat(θ::Number)
```

2D回転行列を構築します。

$$
\bm{R} = \begin{bmatrix}
\cos{\theta} & -\sin{\theta} \\
\sin{\theta} &  \cos{\theta}
\end{bmatrix}
$$

# 例

```jldoctest
julia> rotmat(deg2rad(30))
2×2 Tensor{Tuple{2, 2}, Float64, 2, 4}:
 0.866025  -0.5
 0.5        0.866025
```
