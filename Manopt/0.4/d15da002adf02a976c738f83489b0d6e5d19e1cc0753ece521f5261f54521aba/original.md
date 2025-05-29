```
StopWhenTrustRegionIsExceeded <: StoppingCriterion
```

A functor for testing if the norm of the next iterate in the Steihaug-Toint truncated conjugate gradient method is larger than the trust-region radius $θ \leq \Vert Y_{k}^{*} \Vert_p$ and to end the algorithm when the trust region has been left.

# Fields

  * `reason`: stores a reason of stopping if the stopping criterion has been reached, see [`get_reason`](@ref).

# Constructor

```
StopWhenTrustRegionIsExceeded()
```

initialize the StopWhenTrustRegionIsExceeded functor to indicate to stop after the norm of the next iterate is greater than the trust-region radius.

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
