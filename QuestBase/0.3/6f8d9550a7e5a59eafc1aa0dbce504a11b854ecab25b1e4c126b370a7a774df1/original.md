```julia
rearrange_standard!(eom::QuestBase.DifferentialEquation)
rearrange_standard!(
    eom::QuestBase.DifferentialEquation,
    degree
)

```

Rearranges the differential equations in `eom` to standard form, where the highest derivative of each variable (specified by `degree`, default 2) appears isolated on the left-hand side. Modifies the equations in place.
