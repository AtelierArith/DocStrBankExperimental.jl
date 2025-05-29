```
measure_n(G::AbstractMatrix{T}, a::Int, unit_cell::UnitCell) where {T}
```

軌道種 $a$ に対する平均密度 $\langle \hat{n}_{\sigma,a} \rangle$ を、等時グリーン関数行列 $G_\sigma(\tau,\tau)$ に基づいて測定します。
