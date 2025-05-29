```
convert(
    ::Type{PoincareBallTangentVector},
    p::PoincareHalfSpacePoint,
    X::PoincareHalfSpaceTangentVector
)
```

convert a [`PoincareHalfSpaceTangentVector`](@ref) `X` at `p` to a [`PoincareBallTangentVector`](@ref) on the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ by computing the push forward $π_*(p)[X]$ of the isometry $π$ that maps from the Poincaré half space to the Poincaré ball, cf. [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref).

The formula reads

$$
π_*(p)[X] =
\frac{1}{\lVert \tilde p\rVert^2 + (1+p_n)^2}
\begin{pmatrix}
2X_1\\
⋮\\
2X_{n-1}\\
2⟨X,p⟩
\end{pmatrix}
-
\frac{2}{(\lVert \tilde p\rVert^2 + (1+p_n)^2)^2}
\begin{pmatrix}
2p_1(⟨X,p⟩+X_n)\\
⋮\\
2p_{n-1}(⟨X,p⟩+X_n)\\
(\lVert p \rVert^2-1)(⟨X,p⟩+X_n)
\end{pmatrix}
$$

where $\tilde p = \begin{pmatrix}p_1\\⋮\\p_{n-1}\end{pmatrix}$.
