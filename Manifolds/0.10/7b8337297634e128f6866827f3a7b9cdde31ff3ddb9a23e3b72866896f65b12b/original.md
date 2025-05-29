```
get_coordinates(M::AbstractProjectiveSpace, p, X, B::DefaultOrthonormalBasis{ℝ})
```

Represent the tangent vector $X$ at point $p$ from the [`AbstractProjectiveSpace`](@ref) $M = 𝔽ℙ^n$ in an orthonormal basis by unitarily transforming the hyperplane containing $X$, whose normal is $p$, to the hyperplane whose normal is the $x$-axis.

Given $q = p \overline{λ} + x$, where $λ = \frac{⟨x, p⟩_{\mathrm{F}}}{|⟨x, p⟩_{\mathrm{F}}|}$, $⟨⋅, ⋅⟩_{\mathrm{F}}$ denotes the Frobenius inner product, and $\overline{⋅}$ denotes complex or quaternionic conjugation, the formula for $Y$ is

$$
\begin{pmatrix}0 \\ Y\end{pmatrix} = \left(X - q\frac{2 ⟨q, X⟩_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}\right)\overline{λ}.
$$
