```
previous_level(
    m,
    n::Storage,
    prev_pers::PreviousPeriods{<:NothingPeriod, <:TS.AbstractRepresentativePeriod, Nothing},
    cyclic_pers::CyclicPeriods,
    modeltype::EnergyModel,
)
```

前の運用期間が `Nothing` の場合、前の代表期間は `AbstractRepresentativePeriod` であり、最後の期間も `AbstractRepresentativePeriod` であるとき、時間構造は *代表期間* を含みます。

サイクリックデフォルト制約は、代表期間の繰り返し回数を考慮しながら、*前の* 代表期間の終わりでの値を返します。
