```
delete(stochasticprogram::StochasticProgram, sp_crefs::Vector{<:SPConstraintRef}, scenario_index::Integer)
```

`sp_crefs`に関連付けられたシナリオ依存の決定制約を、`scenario_index`で`stochasticprogram`から削除します。
