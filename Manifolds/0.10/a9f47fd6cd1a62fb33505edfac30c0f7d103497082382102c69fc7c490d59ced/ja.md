```
get_coordinates(M::HeisenbergGroup, p, X, ::DefaultOrthonormalBasis{ℝ,TangentSpaceType})
```

点 `p` における接ベクトル `X` の座標を [`HeisenbergGroup`](@ref) `M` から取得します。行列が与えられたとき

$$
\begin{bmatrix} 1 & \mathbf{a} & c \\
\mathbf{0} & I_n & \mathbf{b} \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$

座標はベクトル $\mathbf{a}$、$\mathbf{b}$ と数 $c$ の連結されたものです。 ```
