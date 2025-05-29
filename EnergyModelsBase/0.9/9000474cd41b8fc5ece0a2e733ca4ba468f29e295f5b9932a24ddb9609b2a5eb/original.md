```
previous_level_sp(
    m,
    n::Storage{CyclicStrategic},
    cyclic_pers::CyclicPeriods{<:TS.AbstractRepresentativePeriod},
    modeltype::EnergyModel,
)
```

When a [`CyclicStrategic`](@ref) `Storage` node is coupled with a `TimeStructure` containing `RepresentativePeriods`, then the function calculates the level at the beginning of the first representative period through the changes in the level in the last representative period.
