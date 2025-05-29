```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods,
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

Returns the level used as previous level of a `Storage` node depending on the type of [`PreviousPeriods`](@ref).

The basic functionality is used in the case when the previous operational period is a `TimePeriod`, in which case it just returns the previous operational period.
