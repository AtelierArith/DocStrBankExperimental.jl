```
get_coordinates(M::HeisenbergMatrices, p, X, ::DefaultOrthonormalBasis{ℝ,TangentSpaceType})
```

点 `p` における接ベクトル `X` の座標を [`HeisenbergMatrices`](@ref) `M` から取得します。行列が次のような場合

$$
\begin{bmatrix} 1 & \mathbf{a} & c \\
\mathbf{0} & I_n & \mathbf{b} \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$

座標は連結されたベクトル $\mathbf{a}$、$\mathbf{b}$、および数 $c$ です。
