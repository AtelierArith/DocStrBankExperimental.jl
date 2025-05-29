```julia
is_rearranged_standard(
    eom::QuestBase.DifferentialEquation
) -> Any
is_rearranged_standard(
    eom::QuestBase.DifferentialEquation,
    degree
) -> Any

```

Checks if the differential equations in `eom` are arranged in standard form, where the highest derivative of each variable appears isolated on the left-hand side. The default degree is 2, corresponding to second-order differential equations.
