```
SteepestDescentCoefficient()
SteepestDescentCoefficient(M::AbstractManifold)
```

Computes an update coefficient for the [`conjugate_gradient_descent`](@ref) algorithm so that is falls back to a [`gradient_descent`](@ref) method, that is

$$
β_k = 0
$$

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`SteepestDescentCoefficient`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

