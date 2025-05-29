```
convert(::Type{HyperboloidTVector}, p::PoincareBallPoint, X::PoincareBallTVector)
convert(::Type{AbstractVector}, p::PoincareBallPoint, X::PoincareBallTVector)
```

Convert the [`PoincareBallTVector`](@ref) `X` from the tangent space at `p` to a [`HyperboloidTVector`](@ref) by computing the push forward of the isometric map, cf. [`convert(::Type{HyperboloidPoint}, p::PoincareBallPoint)`](@ref).

The push forward $π_*(p)$ maps from $ℝ^n$ to a subspace of $ℝ^{n+1}$, the formula reads

$$
π_*(p)[X] = \begin{pmatrix}
    \frac{2X_1}{1-\lVert p \rVert^2} + \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩p_1\\
    ⋮\\
    \frac{2X_n}{1-\lVert p \rVert^2} + \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩p_n\\
    \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩
\end{pmatrix}.
$$
