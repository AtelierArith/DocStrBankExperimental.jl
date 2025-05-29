```
get_coordinates(M::HeisenbergGroup, p, X, ::DefaultOrthonormalBasis{ℝ,TangentSpaceType})
```

Get coordinates of tangent vector `X` at point `p` from the [`HeisenbergGroup`](@ref) `M`. Given a matrix

$$
\begin{bmatrix} 1 & \mathbf{a} & c \\
\mathbf{0} & I_n & \mathbf{b} \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$

the coordinates are concatenated vectors $\mathbf{a}$, $\mathbf{b}$, and number $c$.
