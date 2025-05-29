```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, <:TS.AbstractRepresentativePeriod, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

When the previous operational period is `Nothing`, the previous representative period an `AbstractRepresentativePeriod` and the last period is an `AbstractRepresentativePeriod`, then the time structure *does* include `RepresentativePeriods`.

The cyclic default constraints returns the value at the end of the *previous* representative period while accounting for the number of  repetitions of the representative period.
