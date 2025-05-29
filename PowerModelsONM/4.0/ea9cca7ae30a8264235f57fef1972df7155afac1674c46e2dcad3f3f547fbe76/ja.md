```
variable_generator_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

発電機のオン/オフを切り替えるための変数 $z^{gen}_i,~\forall i \in G$、`relax=false` の場合はバイナリです。`report=true` の場合、変数は解に表示されます。
