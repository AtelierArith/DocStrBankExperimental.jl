```
KKTVectorFieldNormSq{O<:ConstrainedManifoldObjective}
```

Implement the square of the norm of the vectorfield $F$ of the KKT-conditions, inlcuding a slack variable for the inequality constraints, see [`KKTVectorField`](@ref), where this functor applies the norm to. In [LaiYoshise:2024](@cite) this is called the merit function.

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)

# Constructor

```
KKTVectorFieldNormSq(cmo::ConstrainedManifoldObjective)
```

# Example

Define `f = KKTVectorFieldNormSq(cmo)` for some [`ConstrainedManifoldObjective`](@ref) `cmo` and let `N` be the product manifold of $\mathcal M×ℝ^m×ℝ^n×ℝ^m$. Then, you can call this cost as `f(N, q)`, where `q` is a point on `N`.
