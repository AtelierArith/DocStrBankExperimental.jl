```
constraint_unity_pf_inverter_disjunctive(pm::_PM.AbstractIVRModel, nw::Int, i::Int, bus_id::Int, pg, qg, cmax)
```

グリッドフォローイングモードでのインバータの故障電流寄与に関する制約、電流制限のための擬似バイナリを使用しています。
