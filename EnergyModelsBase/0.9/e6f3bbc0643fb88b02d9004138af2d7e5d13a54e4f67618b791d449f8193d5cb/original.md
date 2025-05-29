```
previous_level_sp(
    m,
    n::Storage{<:Cyclic},
    cyclic_pers::CyclicPeriods,
    modeltype
)
```

Returns the previous period in the case of the first operational period (in the first representative period) of a strategic period.

The default functionality in the case of a [`Cyclic`](@ref) storage node in a `TimeStructure` without `RepresentativePeriods` returns the last operational period in the strategic period.
