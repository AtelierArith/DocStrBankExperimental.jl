```
log(G::HeisenbergGroup, p, q)
```

[`HeisenbergGroup`](@ref)群の対数写像を計算します。式は次のようになります。

$$
\log_{\begin{bmatrix} 1 & \mathbf{a}_p & c_p \\
\mathbf{0} & I_n & \mathbf{b}_p \\
0 & \mathbf{0} & 1 \end{bmatrix}}\left(\begin{bmatrix} 1 & \mathbf{a}_q & c_q \\
\mathbf{0} & I_n & \mathbf{b}_q \\
0 & \mathbf{0} & 1 \end{bmatrix}\right) =
\begin{bmatrix} 0 & \mathbf{a}_q - \mathbf{a}_p & c_q - c_p + \mathbf{a}_p⋅\mathbf{b}_p - \mathbf{a}_q⋅\mathbf{b}_q - (\mathbf{a}_q - \mathbf{a}_p)⋅(\mathbf{b}_q - \mathbf{b}_p) / 2 \\
\mathbf{0} & 0_n & \mathbf{b}_q - \mathbf{b}_p \\
0 & \mathbf{0} & 0 \end{bmatrix}
$$

ここで、$I_n$は$n×n$の単位行列、$0_n$は$n×n$のゼロ行列であり、$\mathbf{a}⋅\mathbf{b}$はベクトルのドット積です。
