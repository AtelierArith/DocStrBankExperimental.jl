```
SpecialOrthogonalGroup{T}
```

The special orthogonal group $\mathrm{SO}(n)$ is the Lie group consisting of the [`MatrixMultiplicationGroupOperation`](@ref) on the manifold of rotations [`Rotations`](@extref `Manifolds.Rotations`).

# Constructor

```
SpecialOrthogonalGroup(n::Int; kwargs...)
```

Generate  special orthogonal group $\mathrm{SO}(n)$. All keyword arguments in `kwargs...` are passed on to [`Rotations`](@extref `Manifolds.Rotations`) as well.
