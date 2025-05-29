```
is_conductor(C::Hecke.ClassField, m::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, inf_plc::Vector{InfPlc}=InfPlc[]; check) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Vector{InfPlc}
```

(m, inf_plc) が $C$ に対応するアーベル拡張の導体であるかどうかをチェックします。`check` が `false` の場合、与えられた剰余が導体の倍数であると仮定します。これは通常、導体を計算するよりも速いです。
