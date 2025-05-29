```
previous_level_sp(
    m,
    n::Storage{<:Cyclic},
    cyclic_pers::CyclicPeriods,
    modeltype
)
```

戦略的期間の最初の代表的期間における最初の運用期間の場合、前の期間を返します。

`RepresentativePeriods`なしの`TimeStructure`における[`Cyclic`](@ref)ストレージノードの場合のデフォルト機能は、戦略的期間の最後の運用期間を返します。
