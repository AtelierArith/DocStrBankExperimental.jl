```
inv(G::SpecialEuclideanGroup, g)
inv(G::SpecialEuclideanGroup, h, g)
```

Compute the inverse element of a $g ∈ \mathrm{SE}(n)$ from the [`SpecialEuclideanGroup`](@ref)`(n)`.

In affine form, $g = \begin{pmatrix} r & t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}$, where $\mathbf{0}_n ∈ ℝ^n$ denotes the vector containing zeros.

The inverse reads

$$
g^{-1} = \begin{pmatrix} r^{\mathrm{T}} & -r^{\mathrm{T}}t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}.
$$

This computation can be done in-place of `h`.
