```
log(G, g)
log!(G, X, g)
```

Compute the Lie group logarithm function on the [`OrthogonalGroup`](@ref) $\mathrm{O}(2)$ or [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(2)$, where `e` is the [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) for dispatch.

For the two-dimensional case, any rotation matrix $g$ can be represented as $\begin{pmatrix} \cos(α) & -\sin(α)\\ \sin(α) & \cos(α)\end{pmatrix}$. For the [`SpecialOrthogonalGroup`](@ref), $g$ might also include reflections.

The logarithm is then

$$
\log_{\mathcal G}(g) =  \begin{pmatrix} 0 & α\\ -α & 0\end{pmatrix}.
$$

This result can be computed in-place of `X`

Note the logarithmic map is only locally around the identity uniquely determined. Especially, since $\mathrm{O}(2)$ consists of two disjoint connected components and the exponential map is smooth, for any $g$ in the other component, the logarithmic map is defined, but not the inverse of the exponential map.
