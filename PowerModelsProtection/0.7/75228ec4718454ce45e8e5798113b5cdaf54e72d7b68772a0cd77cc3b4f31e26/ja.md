```
constraint_i_inverter_vs(pm::_PM.AbstractIVRModel, n::Int, i::Int, bus_id::Int, vs, pg, qg, cm)
```

グリッドフォローイングモードにおけるインバータの故障電流寄与に関する制約であり、インバータの電流調整ループが遅く動作することを前提としています。
