```
constraint_pf_inverter_vs(pm::_PM.AbstractIVRModel, n::Int, i::Int, bus_id::Int, vs, pg, qg, cmax)
```

グリッドフォローイングモードにおけるインバータの故障電流寄与に関する制約で、低ゼロ端子電圧を処理するための実電圧降下を伴います。
