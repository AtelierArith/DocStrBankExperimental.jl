```
StopWhenRelativeResidualLess <: StoppingCriterion
```

Stop when re relative residual in the [`conjugate_residual`](@ref) is below a certain threshold, i.e.

$$
  \frac{\lVert r^{(k)} \rVert}{c} ≤ ε,
$$

where $c = \lVert b \rVert$ of the initial vector from the vector field in $\mathcal A(p)[X] + b(p) = 0_p$, from the [`conjugate_residual`](@ref)

# Fields

  * `at_iteration` indicates at which iteration (including `i=0`) the stopping criterion was fulfilled and is `-1` while it is not fulfilled.
  * `c`: the initial norm
  * `ε`: the threshold
  * `norm_rk`: the last computed norm of the residual

# Constructor

```
StopWhenRelativeResidualLess(c, ε; norm_r = 2*c*ε)
```

Initialise the stopping criterion.

!!! note
    The initial norm of the vector field $c = \lVert b \rVert$ that is stored internally is updated on initialisation, that is, if this stopping criterion is called with `k<=0`.

