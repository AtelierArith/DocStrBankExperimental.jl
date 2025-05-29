```
StopWhenModelIncreased <: StoppingCriterion
```

A functor for testing if the curvature of the model value increased.

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `model_value`stre the last model value
  * `inc_model_value` store the model value that increased

# Constructor

```
StopWhenModelIncreased()
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
