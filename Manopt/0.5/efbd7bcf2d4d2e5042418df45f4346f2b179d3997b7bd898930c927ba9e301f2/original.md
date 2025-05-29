```
StopWhenRelativeResidualLess <: StoppingCriterion
```

Stop when re relative residual in the [`conjugate_residual`](@ref) is below a certain threshold, i.e.

$$
\displaystyle\frac{\lVert r^{(k) \rVert_{}}{c} ≤ ε,
$$

where $c = \lVert b \rVert_{}$ of the initial vector from the vector field in $\mathcal A(p)[X] + b(p) = 0_p$, from the [`conjugate_residual`](@ref)

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `c`: the initial norm
  * `ε`: the threshold
  * `norm_rk`: the last computed norm of the residual

# Constructor

```
StopWhenRelativeResidualLess(c, ε; norm_r = 2*c*ε)
```

Initialise the stopping criterion.

!!! note
    The initial norm of the vector field $c = \lVert b \rVert_{}$ that is stored internally is updated on initialisation, that is, if this stopping criterion is called with `k<=0`.

