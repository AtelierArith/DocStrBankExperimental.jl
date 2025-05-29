```
exp(M::HeisenbergGroup, p, X)
```

左不変メトリックを持つ[`HeisenbergGroup`](@ref) `M`上の指数写像。式は次のように表されます。

$$
\exp_{\begin{bmatrix} 1 & \mathbf{a}_p & c_p \\
\mathbf{0} & I_n & \mathbf{b}_p \\
0 & \mathbf{0} & 1 \end{bmatrix}}\left(\begin{bmatrix} 0 & \mathbf{a}_X & c_X \\
\mathbf{0} & 0_n & \mathbf{b}_X \\
0 & \mathbf{0} & 0 \end{bmatrix}\right) =
\begin{bmatrix} 1 & \mathbf{a}_p + \mathbf{a}_X & c_p + c_X + \mathbf{a}_X⋅\mathbf{b}_X/2 + \mathbf{a}_p⋅\mathbf{b}_X \\
\mathbf{0} & I_n & \mathbf{b}_p + \mathbf{b}_X \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$

ここで、$I_n$は$n×n$の単位行列、$0_n$は$n×n$の零行列であり、$\mathbf{a}⋅\mathbf{b}$はベクトルのドット積です。
