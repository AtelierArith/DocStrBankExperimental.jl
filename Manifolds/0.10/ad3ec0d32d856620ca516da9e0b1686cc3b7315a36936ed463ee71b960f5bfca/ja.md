```
apply(A::ComplexPlanarRotation, g::Complex, p)
```

点 `p` を群要素 `g` によって [`Euclidean(2)`](@ref) 多様体から回転させます。式は次のようになります。

$$
p_{rot} =  \begin{bmatrix}
\cos(θ) & \sin(θ)\\
-\sin(θ) & \cos(θ)
\end{bmatrix} p,
$$

ここで `θ` は複素数 `g` の引数です。
