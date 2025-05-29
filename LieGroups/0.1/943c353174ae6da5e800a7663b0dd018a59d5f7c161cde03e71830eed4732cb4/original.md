```
log(G, g)
log!(G, X, g)
```

Compute the Lie group logarithm function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(3)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(3)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

Here, $\exp_{\mathcal G}(X) = g$ is inverted using the [Rodrigues' rotation formula](https://en.wikipedia.org/wiki/Olinde_Rodrigues)

$$
\exp_{\mathcal G}(X) = I_3 + \frac{\sin}{α}X + \frac{(1 - \cos)}{α^2}X^2,
$$

For $α ∉ \{ 0, π \}$ we obtain $X$ from the observation that

$$
\mathrm{tr}(g) = 1 + 2\cos(α)
\qquad\text{ and }\qquad
\frac{1}{2}(g-g^\mathrm{T}) = \sin(α)X.
$$

For $α = 0$ we have $g = I_3$ and $X = 0$.

For $α = π$ we have to solve $X^2 = \frac{1}{2}(g-I_3)$, where $X$ is skew-symmetric and hence we have to solve for three unknowns.

$$
\log_{\mathcal G}(g) = X.
$$

This result can be computed in-place of `X`

Note the logarithmic map is only locally around the identity uniquely determined. Especially, since $\mathrm{O}(3)$ consists of two disjoint connected components and the exponential map is smooth, for any $g$ in the other component, the logarithmic map is defined, but not the inverse of the exponential map.
