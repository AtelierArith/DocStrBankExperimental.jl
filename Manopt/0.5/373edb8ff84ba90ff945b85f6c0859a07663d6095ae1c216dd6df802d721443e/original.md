```
ConjugateDescentCoefficient()
ConjugateDescentCoefficient(M::AbstractManifold)
```

Compute the (classical) conjugate gradient coefficient based on [Fletcher:1987](@cite) adapted to manifolds

Denote the last iterate and gradient by $p_k,X_k$, the current iterate and gradient by $p_{k+1}, X_{k+1}$, respectively, as well as the last update direction by $δ_k$.

Then the coefficient reads

$$
β_k = \frac{\lVert X_{k+1} \rVert_{p_{k+1}}^2}{⟨-δ_k,X_k⟩_{p_k}}
$$

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`ConjugateDescentCoefficientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

