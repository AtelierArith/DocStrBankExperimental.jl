```
exp(G, X)
exp!(G, g, X)
```

Compute the Lie group exponential function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(3)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(3)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

Since the Lie algebra of both groups agrees and consist of the set of skew symmetric matrices, the $3×3$ skew symmetric matrices are of the form

$$
    X = \begin{pmatrix} 0 & -c & b\\ c & 0 & -a\\ -b & a & 0\end{pmatrix},
$$

for some $a, b, c ∈ ℝ$. To compute the exponential, the [Rodrigues' rotation formula](https://en.wikipedia.org/wiki/Olinde_Rodrigues) can be used. With $α = \sqrt{a^2+b^2+c^2} = \frac{1}{\sqrt{2}}\lVert X \rVert_{}$ we obtain for $α ≠ 0$

$$
\exp_{\mathcal G}(X) = I_3 + \frac{\sin}{α}X + \frac{(1 - \cos)}{α^2}X^2,
$$

and \exp*{\mathcal G}(X) = I*3`` otherwise.

This result can be computed in-place of `g`.

Note that since $\mathrm{SO}(3)$ consists of two disjoint connected components and the exponential map is smooth, the result $g$ always lies in the connected component of the identity.
