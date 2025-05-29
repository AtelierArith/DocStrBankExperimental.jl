```
OrthogonalGroup{T}
```

The orthogonal group $\mathrm{O}(n)$ is the Lie group consisting of the [`MatrixMultiplicationGroupOperation`](@ref) on the manifold of rotations [`OrthogonalMatrices`](@extref `Manifolds.OrthogonalMatrices`).

# Constructor

```
OrthogonalGroup(n::Int; kwargs...)
```

Generate  orthogonal group $\mathrm{O}(n)$. All keyword arguments in `kwargs...` are passed on to [`OrthogonalMatrices`](@extref `Manifolds.OrthogonalMatrices`) as well.
