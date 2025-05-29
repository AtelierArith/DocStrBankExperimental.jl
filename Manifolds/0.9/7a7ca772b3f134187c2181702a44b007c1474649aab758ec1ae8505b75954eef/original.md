```
convert(::Type{PoincareHalfSpaceTVector}, p::PoincareBallPoint, X::PoincareBallTVector)
```

convert a [`PoincareBallTVector`](@ref) `X` at `p` to a [`PoincareHalfSpacePoint`](@ref) on the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ by computing the push forward $π_*(p)[X]$ of the isometry $π$ that maps from the Poincaré ball to the Poincaré half space, cf. [`convert(::Type{PoincareHalfSpacePoint}, ::PoincareBallPoint)`](@ref).

The formula reads

$$
π_*(p)[X] =
\frac{1}{\lVert \tilde p\rVert^2 + (1-p_n)^2}
\begin{pmatrix}
2X_1\\
⋮\\
2X_{n-1}\\
-2⟨X,p⟩
\end{pmatrix}
-
\frac{2}{(\lVert \tilde p\rVert^2 + (1-p_n)^2)^2}
\begin{pmatrix}
2p_1(⟨X,p⟩-X_n)\\
⋮\\
2p_{n-1}(⟨X,p⟩-X_n)\\
(\lVert p \rVert^2-1)(⟨X,p⟩-X_n)
\end{pmatrix}
$$

where $\tilde p = \begin{pmatrix}p_1\\⋮\\p_{n-1}\end{pmatrix}$.
