```
exp(M::HeisenbergGroup, p, X)
```

Exponential map on the [`HeisenbergGroup`](@ref) `M` with the left-invariant metric. The expression reads

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

where $I_n$ is the $n×n$ identity matrix, $0_n$ is the $n×n$ zero matrix and $\mathbf{a}⋅\mathbf{b}$ is dot product of vectors.
