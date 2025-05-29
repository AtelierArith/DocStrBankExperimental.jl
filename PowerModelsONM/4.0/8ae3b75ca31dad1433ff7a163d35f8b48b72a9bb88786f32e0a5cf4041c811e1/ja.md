```
variable_robust_inverter_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, report::Bool=true)
```

DER（ストレージまたは発電機）がグリッド形成モード（1）またはグリッドフォローイングモード（0）にあるかどうかを示すためのロバストmld（外部）問題の解。
