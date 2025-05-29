```julia
first_order_transform!(
    diff_eom::QuestBase.DifferentialEquation,
    time
)

```

Transforms a higher-order differential equation system into an equivalent first-order system by introducing additional variables. Modifies the system in place. The `time` parameter specifies the independent variable used for differentiation.
