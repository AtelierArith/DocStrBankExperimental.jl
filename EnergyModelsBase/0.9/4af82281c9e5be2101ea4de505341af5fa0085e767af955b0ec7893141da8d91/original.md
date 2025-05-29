```
previous_level(
    m,
    n::Storage{CyclicRepresentative},
    prev_pers::PreviousPeriods{<:NothingPeriod, <:TS.AbstractRepresentativePeriod, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

When the previous operational period is `Nothing` and the previous representative period an `AbstractRepresentativePeriod` then the time structure *does* include `RepresentativePeriods`.

The cyclic constraint for a [`CyclicRepresentative`](@ref) storage nodereturns the value at the end of the *current* representative period.
