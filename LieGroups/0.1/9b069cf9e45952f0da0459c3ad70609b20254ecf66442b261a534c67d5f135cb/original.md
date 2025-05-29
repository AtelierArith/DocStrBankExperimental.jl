```
UnitaryGroup{T}
```

The special orthogonal group $\mathrm{U}(n)$ is the Lie group consisting of the [`MatrixMultiplicationGroupOperation`](@ref) on the manifold of rotations [`UnitaryMatrices`](@extref `Manifolds.GeneralUnitaryMatrices`) with absolute value of the determinant equal to one.

# Constructor

```
UnitaryGroup(n::Int, 𝔽::AbstractNumbers=ℂ; kwargs...)
```

Generate unitary group $\mathrm{U}(n)$. All keyword arguments in `kwargs...` are passed on to [`Rotations`](@extref `Manifolds.Rotations`) as well.
