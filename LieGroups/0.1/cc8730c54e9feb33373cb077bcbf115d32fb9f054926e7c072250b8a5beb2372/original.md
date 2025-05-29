```
exp(G, X)
exp!(G, g, X)
```

Compute the Lie group exponential function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(2)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(2)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

Since the Lie algebra of both groups agrees and consist of the set of skew symmetric matrices, these simplify for the case of $2×2$ matrices to $X=\begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$, for some $α∈ℝ$.

Their exponential is

$$
\exp_{\mathcal G}(X) =  \begin{pmatrix} \cos(α) & -\sin(α)\\ \sin(α) & \cos(α)\end{pmatrix}.
$$

This result can be computed in-place of `g`.

Note that since $\mathrm{O}(2)$ consists of two disjoint connected components and the exponential map is smooth, the result $g$ always lies in the connected component of the identity.
