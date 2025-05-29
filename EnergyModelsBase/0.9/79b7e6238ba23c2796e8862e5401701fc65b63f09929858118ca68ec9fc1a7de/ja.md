```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods,
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

`Storage`ノードの前のレベルを[`PreviousPeriods`](@ref)のタイプに応じて返します。

基本的な機能は、前の運用期間が`TimePeriod`である場合に使用され、その場合は単に前の運用期間を返します。
