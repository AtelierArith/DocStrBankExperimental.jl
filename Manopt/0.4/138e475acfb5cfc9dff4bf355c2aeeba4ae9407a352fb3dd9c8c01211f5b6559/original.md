```
AdaptiveRagularizationWithCubicsModelObjective
```

A model for the adaptive regularization with Cubics

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
       +  \frac{σ}{3} \lVert X \rVert^3,
$$

cf. Eq. (33) in [AgarwalBoumalBullinsCartis:2020](@cite)

# Fields

  * `objective`: an [`AbstractManifoldHessianObjective`](@ref) proving $f$, its gradient and Hessian
  * `σ`:         the current (cubic) regularization parameter

# Constructors

```
AdaptiveRagularizationWithCubicsModelObjective(mho, σ=1.0)
```

with either an [`AbstractManifoldHessianObjective`](@ref) `objective` or an decorator containing such an objective.
