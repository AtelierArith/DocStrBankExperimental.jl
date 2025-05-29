```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, Nothing, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

When the previous operational and representative period are `Nothing` and the storage node is an [`AccumulatingEmissions`](@ref) storage node, the function returns a value of 0.
