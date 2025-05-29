```
previous_level_sp(
    m,
    n::Storage{CyclicStrategic},
    cyclic_pers::CyclicPeriods{<:TS.AbstractRepresentativePeriod},
    modeltype::EnergyModel,
)
```

[`CyclicStrategic`](@ref) `Storage` ノードが `RepresentativePeriods` を含む `TimeStructure` と結合されると、関数は最後の代表期間におけるレベルの変化を通じて、最初の代表期間の始まりにおけるレベルを計算します。
