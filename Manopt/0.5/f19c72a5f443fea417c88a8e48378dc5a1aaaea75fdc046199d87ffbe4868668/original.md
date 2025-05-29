```
TrustRegionModelObjective{O<:AbstractManifoldHessianObjective} <: AbstractManifoldSubObjective{O}
```

A trust region model of the form

$$
    m(X) = f(p) + ⟨\operatorname{grad} f(p), X⟩_p + \frac{1}(2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
$$

# Fields

  * `objective`: an [`AbstractManifoldHessianObjective`](@ref) proving $f$, its gradient and Hessian

# Constructors

```
TrustRegionModelObjective(objective)
```

with either an [`AbstractManifoldHessianObjective`](@ref) `objective` or an decorator containing such an objective
