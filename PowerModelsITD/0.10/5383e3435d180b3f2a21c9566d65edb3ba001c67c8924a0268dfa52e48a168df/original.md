```
function objective_itd_min_fuel_pwl_distribution_load_setpoint_delta_simple(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractPowerModel,
    pmd::_PMD.AbstractUnbalancedPowerModel
)
```

Fuel cost minimization objective with piecewise linear terms in transmission and load setpoint delta (continuous load shed) for distribution.
