```
get_vector(M::HeisenbergMatrices, p, Xⁱ, ::DefaultOrthonormalBasis{ℝ,TangentSpaceType})
```

点 `p` での座標 `Xⁱ` を持つ接ベクトルを [`HeisenbergMatrices`](@ref) `M` から取得します。座標のベクトル $\begin{bmatrix}\mathbb{a} & \mathbb{b} & c\end{bmatrix}$ が与えられたとき、接ベクトルは次のようになります。

$$
\begin{bmatrix} 1 & \mathbf{a} & c \\
\mathbf{0} & I_n & \mathbf{b} \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$
