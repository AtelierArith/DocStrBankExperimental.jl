```
get_coordinates(M::AbstractSphere{ℝ}, p, X, B::DefaultOrthonormalBasis)
```

Represent the tangent vector `X` at point `p` from the [`AbstractSphere`](@ref) `M` in an orthonormal basis by rotating the hyperplane containing `X` to a hyperplane whose normal is the $x$-axis.

Given $q = p λ + x$, where $λ = \operatorname{sgn}(⟨x, p⟩)$, and $⟨⋅, ⋅⟩_{\mathrm{F}}$ denotes the Frobenius inner product, the formula for $Y$ is

$$
\begin{pmatrix}0 \\ Y\end{pmatrix} = X - q\frac{2 ⟨q, X⟩_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}.
$$
