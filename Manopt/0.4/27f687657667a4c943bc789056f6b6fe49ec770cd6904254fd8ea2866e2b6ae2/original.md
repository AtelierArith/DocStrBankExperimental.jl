```
StopWhenModelIncreased <: StoppingCriterion
```

A functor for testing if the curvature of the model value increased.

# Fields

  * `reason`: stores a reason of stopping if the stopping criterion has been reached, see [`get_reason`](@ref).

# Constructor

```
StopWhenModelIncreased()
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
