```
log(G::HeisenbergGroup, p, q)
```

Compute the logarithmic map on the [`HeisenbergGroup`](@ref) group. The formula reads

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

where $I_n$ is the $n×n$ identity matrix, $0_n$ is the $n×n$ zero matrix and $\mathbf{a}⋅\mathbf{b}$ is dot product of vectors.
