```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, Nothing, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

前の運用期間と代表期間が `Nothing` の場合、関数は戦略的期間内の周期的制約を返します。これは、メソッドの曖昧さを避けるためにサブ関数 [`previous_level_sp`](@ref) を呼び出すことで実現されます。
