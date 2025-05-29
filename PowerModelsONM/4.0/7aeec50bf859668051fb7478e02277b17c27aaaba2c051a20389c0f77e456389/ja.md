```
variable_load_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

負荷のオン/オフを切り替えるための変数 $z^{d}_i,~\forall i \in L$、`relax=false` の場合はバイナリです。`report=true` の場合、変数は解に現れます。
