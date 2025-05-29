```
FletcherReevesCoefficient()
FletcherReevesCoefficient(M::AbstractManifold)
```

Computes an update coefficient for the [`conjugate_gradient_descent`](@ref) algorithm based on [FletcherReeves:1964](@cite) adapted to manifolds

Denote the last iterate and gradient by $p_k,X_k$, the current iterate and gradient by $p_{k+1}, X_{k+1}$, respectively, as well as the last update direction by $δ_k$.

Then the coefficient reads

$$
β_k =
\frac{\lVert X_{k+1} \rVert_{p_{k+1}}^2}{\lVert X_k \rVert_{p_{k}}^2}.
$$

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`FletcherReevesCoefficientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

