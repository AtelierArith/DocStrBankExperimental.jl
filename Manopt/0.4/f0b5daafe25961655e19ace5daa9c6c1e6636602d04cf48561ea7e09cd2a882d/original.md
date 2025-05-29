```
StopWhenCurvatureIsNegative <: StoppingCriterion
```

A functor for testing if the curvature of the model is negative, $⟨δ_k, \operatorname{Hess}[F](\delta_k)⟩_p ≦ 0$. In this case, the model is not strictly convex, and the stepsize as computed does not yield a reduction of the model.

# Fields

  * `reason`: stores a reason of stopping if the stopping criterion has been reached, see [`get_reason`](@ref).

# Constructor

```
StopWhenCurvatureIsNegative()
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
