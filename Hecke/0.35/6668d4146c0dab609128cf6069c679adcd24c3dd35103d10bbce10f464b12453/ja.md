```
ray_class_group(m::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, inf_plc::Vector{InfPlc}; n_quo::Int, lp::Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}) -> FinGenAbGroup, MapRayClassGrp
```

理想 $m$ と $K$ の無限位の集合が与えられたとき、この関数は対応するレイ類群を抽象群 $\mathcal {Cl}_m$ として返し、群から $m$ と互いに素な $K$ の理想の群への写像を返します。`n_quo` が設定されている場合、`n_quo` で割った群を返します。$m$ の因数分解はキーワード引数 `lp` で与えることができます。
