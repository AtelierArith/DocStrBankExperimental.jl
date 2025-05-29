```
previous_level_sp(
    m,
    n::Storage{CyclicRepresentative},
    cyclic_pers::CyclicPeriods{<:TS.AbstractRepresentativePeriod},
    modeltype::EnergyModel,
)
```

When a [`CyclicRepresentative`](@ref) `Storage` node is coupled with a `TimeStructure` containing `RepresentativePeriods`, then the function returns the previous level as the level at the end of the current representative period.
