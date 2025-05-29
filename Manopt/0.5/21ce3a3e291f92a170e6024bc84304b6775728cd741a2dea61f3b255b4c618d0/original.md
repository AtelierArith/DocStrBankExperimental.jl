```
StopWhenTrustRegionIsExceeded <: StoppingCriterion
```

A functor for testing if the norm of the next iterate in the Steihaug-Toint truncated conjugate gradient method is larger than the trust-region radius $θ ≤ \lVert Y^{(k)}^{*} \rVert_{p^{(k)}}$ and to end the algorithm when the trust region has been left.

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `trr` the trust region radius
  * `YPY` the computed norm of $Y$.

# Constructor

```
StopWhenTrustRegionIsExceeded()
```

initialize the StopWhenTrustRegionIsExceeded functor to indicate to stop after the norm of the next iterate is greater than the trust-region radius.

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
