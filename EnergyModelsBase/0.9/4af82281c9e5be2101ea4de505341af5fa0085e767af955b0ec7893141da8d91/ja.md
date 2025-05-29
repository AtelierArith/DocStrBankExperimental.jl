```
previous_level(
    m,
    n::Storage{CyclicRepresentative},
    prev_pers::PreviousPeriods{<:NothingPeriod, <:TS.AbstractRepresentativePeriod, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

前の運用期間が `Nothing` で、前の代表期間が `AbstractRepresentativePeriod` の場合、時間構造には *代表期間* が含まれます。

[`CyclicRepresentative`](@ref) ストレージノードのための周期的制約は、*現在の* 代表期間の終わりでの値を返します。
