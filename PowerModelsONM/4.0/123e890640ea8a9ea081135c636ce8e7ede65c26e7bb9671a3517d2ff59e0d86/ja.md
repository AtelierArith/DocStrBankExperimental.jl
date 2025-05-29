```
variable_inverter_indicator(pm::AbstractUnbalancedPowerModel; nw::Int=nw_id_default, relax::Bool=false, report::Bool=true)
```

DER（ストレージまたは発電機）がグリッド形成モード（1）またはグリッドフォローイングモード（0）にあるかどうかを示すための変数。バイナリは `relax=false` の場合。変数は `report=true` の場合に解に現れます。"inverter" がデバイス上で GRID_FOLLOWING の場合、インバータ変数は定数になります。
