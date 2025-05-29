```julia
calc_two_sigma_bound_test(
    state_errors,
    variances;
    dims,
    atol
)

```

Innovation magnitude bound test (2σ-bound-test)

Tests if approximately 95% of state values lie within the ⨦2σ bound. The parameter     dims must be the dimenstion of Monte Carlo runs or the time dimension.
