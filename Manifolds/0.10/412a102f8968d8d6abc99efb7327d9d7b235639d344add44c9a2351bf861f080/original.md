```
get_vector(M::HeisenbergMatrices, p, Xⁱ, ::DefaultOrthonormalBasis{ℝ,TangentSpaceType})
```

Get tangent vector with coordinates `Xⁱ` at point `p` from the [`HeisenbergMatrices`](@ref) `M`. Given a vector of coordinates $\begin{bmatrix}\mathbb{a} & \mathbb{b} & c\end{bmatrix}$ the tangent vector is equal to

$$
\begin{bmatrix} 1 & \mathbf{a} & c \\
\mathbf{0} & I_n & \mathbf{b} \\
0 & \mathbf{0} & 1 \end{bmatrix}
$$
