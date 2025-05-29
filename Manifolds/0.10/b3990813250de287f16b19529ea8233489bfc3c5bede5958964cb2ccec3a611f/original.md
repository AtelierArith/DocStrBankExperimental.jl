```
get_vector(M::AbstractSphere{ℝ}, p, X, B::DefaultOrthonormalBasis)
```

Convert a one-dimensional vector of coefficients `X` in the basis `B` of the tangent space at `p` on the [`AbstractSphere`](@ref) `M` to a tangent vector `Y` at `p` by rotating the hyperplane containing `X`, whose normal is the $x$-axis, to the hyperplane whose normal is `p`.

Given $q = p λ + x$, where $λ = \operatorname{sgn}(⟨x, p⟩)$, and $⟨⋅, ⋅⟩_{\mathrm{F}}$ denotes the Frobenius inner product, the formula for $Y$ is

$$
Y = X - q\frac{2 \left\langle q, \begin{pmatrix}0 \\ X\end{pmatrix}\right\rangle_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}.
$$
