```
measure_double_occ(Gup::AbstractMatrix{T}, Gdn::AbstractMatrix{T}, a::Int, unit_cell::UnitCell) where {T}
```

軌道種 $a$ に対して、スピンアップおよびスピンダウンの等時グリーン関数行列 $G_\uparrow(\tau,\tau)$ および $G_\downarrow(\tau,\tau)$ が与えられたとき、二重占有度 $\langle \hat{n}_{\uparrow,a} \hat{n}_{\downarrow,a} \rangle$ を測定します。
