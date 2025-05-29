```
ManifoldHessianObjective{T<:AbstractEvaluationType,C,G,H,Pre} <: AbstractManifoldHessianObjective{T,C,G,H}
```

specify a problem for Hessian based algorithms.

# Fields

  * `cost`:           a function $f:\mathcal M→ℝ$ to minimize
  * `gradient`:       the gradient $\operatorname{grad}f:\mathcal M → \mathcal T\mathcal M$ of the cost function $f$
  * `hessian`:        the Hessian $\operatorname{Hess}f(x)[⋅]: \mathcal T_{x} \mathcal M → \mathcal T_{x} \mathcal M$ of the cost function $f$
  * `preconditioner`: the symmetric, positive definite preconditioner as an approximation of the inverse of the Hessian of $f$, a map with the same input variables as the `hessian` to numerically stabilize iterations when the Hessian is ill-conditioned

Depending on the [`AbstractEvaluationType`](@ref) `T` the gradient and can have to forms

  * as a function `(M, p) -> X`  and `(M, p, X) -> Y`, resp., an [`AllocatingEvaluation`](@ref)
  * as a function `(M, X, p) -> X` and (M, Y, p, X), resp., an [`InplaceEvaluation`](@ref)

# Constructor

```
ManifoldHessianObjective(f, grad_f, Hess_f, preconditioner = (M, p, X) -> X;
    evaluation=AllocatingEvaluation())
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
