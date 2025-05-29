```
get_vector(M::AbstractProjectiveSpace, p, X, B::DefaultOrthonormalBasis{ℝ})
```

Convert a one-dimensional vector of coefficients $X$ in the basis `B` of the tangent space at $p$ on the [`AbstractProjectiveSpace`](@ref) $M=𝔽ℙ^n$ to a tangent vector $Y$ at $p$ by unitarily transforming the hyperplane containing $X$, whose normal is the $x$-axis, to the hyperplane whose normal is $p$.

Given $q = p \overline{λ} + x$, where $λ = \frac{⟨x, p⟩_{\mathrm{F}}}{|⟨x, p⟩_{\mathrm{F}}|}$, $⟨⋅, ⋅⟩_{\mathrm{F}}$ denotes the Frobenius inner product, and $\overline{⋅}$ denotes complex or quaternionic conjugation, the formula for $Y$ is

$$
Y = \left(X - q\frac{2 \left\langle q, \begin{pmatrix}0 \\ X\end{pmatrix}\right\rangle_{\mathrm{F}}}{⟨q, q⟩_{\mathrm{F}}}\right) λ.
$$
