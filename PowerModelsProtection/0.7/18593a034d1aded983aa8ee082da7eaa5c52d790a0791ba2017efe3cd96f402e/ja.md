```
constraint_i_inverter(pm::_PM.AbstractPowerModel; nw::Int=nw_id_default)
```

グリッドフォローイングモードでのインバータの故障電流寄与に関する制約。インバータの電流調整ループが遅く動作することを前提としています。
