```
StopWhenCurvatureIsNegative <: StoppingCriterion
```

A functor for testing if the curvature of the model is negative, $⟨δ_k, \operatorname{Hess} F(p)[δ_k]⟩_p ≦ 0$. In this case, the model is not strictly convex, and the stepsize as computed does not yield a reduction of the model.

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `value` store the value of the inner product.
  * `reason`: stores a reason of stopping if the stopping criterion has been reached, see [`get_reason`](@ref).

# Constructor

```
StopWhenCurvatureIsNegative()
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
