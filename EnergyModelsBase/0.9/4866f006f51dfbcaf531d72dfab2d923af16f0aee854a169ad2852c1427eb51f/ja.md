```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, Nothing, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

前の運用期間と代表期間が`Nothing`で、ストレージノードが[`AccumulatingEmissions`](@ref)ストレージノードである場合、関数は0の値を返します。
