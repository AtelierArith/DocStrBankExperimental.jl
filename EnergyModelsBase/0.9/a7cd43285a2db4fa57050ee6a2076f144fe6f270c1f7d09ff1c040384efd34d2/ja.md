```
previous_level_sp(
    m,
    n::Storage{CyclicRepresentative},
    cyclic_pers::CyclicPeriods{<:TS.AbstractRepresentativePeriod},
    modeltype::EnergyModel,
)
```

[`CyclicRepresentative`](@ref) `Storage` ノードが `RepresentativePeriods` を含む `TimeStructure` と結合されると、関数は現在の代表期間の終了時のレベルとして前のレベルを返します。
