```
variable_bus_voltage_indicator(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

バスのオン/オフを切り替えるための変数 $z^{bus}_i,~\forall i \in N$、`relax=false` の場合はバイナリです。`report=true` の場合、変数は解に現れます。
