```
SpecialUnitaryGroup{T}
```

The special orthogonal group $\mathrm{SU}(n)$ is the Lie group consisting of the [`MatrixMultiplicationGroupOperation`](@ref) on the manifold of rotations [`GeneralUnitaryMatrices`](@extref `Manifolds.GeneralUnitaryMatrices`) with determinant one.

# Constructor

```
SpecialUnitaryGroup(n::Int; kwargs...)
```

Generate special unitary group $\mathrm{SU}(n)$. All keyword arguments in `kwargs...` are passed on to [`Rotations`](@extref `Manifolds.Rotations`) as well.
