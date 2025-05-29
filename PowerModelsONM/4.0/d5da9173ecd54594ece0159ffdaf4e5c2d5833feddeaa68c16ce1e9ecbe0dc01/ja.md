```
variable_storage_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

ストレージのオン/オフを切り替えるための変数 $z^{strg}_i,~\forall i \in E$、`relax=false` の場合はバイナリです。`report=true` の場合、変数は解に現れます。
