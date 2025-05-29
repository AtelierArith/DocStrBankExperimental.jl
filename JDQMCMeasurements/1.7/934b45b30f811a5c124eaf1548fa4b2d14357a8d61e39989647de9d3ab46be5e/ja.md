```
measure_N(G::AbstractMatrix{T}, a::Int, unit_cell::UnitCell) where {T}
```

軌道種 $a$ における全粒子数 $\langle \hat{N}_{\sigma,a} \rangle$ を、等時グリーン関数行列 $G_\sigma(\tau,\tau)$ に基づいて測定します。
