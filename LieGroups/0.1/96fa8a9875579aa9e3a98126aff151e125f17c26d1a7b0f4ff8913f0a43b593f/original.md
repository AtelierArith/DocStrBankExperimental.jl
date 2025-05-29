```
GeneralLinearGroup{𝔽,T}
```

The general linear group $\mathrm{GL}(n)$ is the set of all invertible matrices

$$
\mathrm{GL}(n) = \bigl\{ M ∈ 𝔽^{n×n}\ \big|\ \mathrm{det}(M) ≠ 0\bigr \},
\qquad 𝔽 ∈ \{ ℝ, ℂ \},
$$

equipped with the [`MatrixMultiplicationGroupOperation`](@ref) as the group operation.

The set of invertible matrices is a Riemannian manifold, since it inherits its structure from the embedding as an open subset of the space of matrices $ℝ^{n×n}$.

# Constructor

```
GeneralLinearGroup(n::Int; field=ℝ, kwargs...)
```

Generate the general linear group on $𝔽^{n×n}$. All keyword arguments in `kwargs...` are passed on to [`InvertibleMatrices`](@extref `Manifolds.InvertibleMatrices`).
