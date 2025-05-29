```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, Nothing, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

When the previous operational and representative period are `Nothing`, the function returns the cyclic constraints within a strategic period. This is achieved through calling a subfunction [`previous_level_sp`](@ref) to avoid method ambiguities.
