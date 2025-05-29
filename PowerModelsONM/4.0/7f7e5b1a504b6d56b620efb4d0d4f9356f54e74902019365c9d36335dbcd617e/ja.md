```
constraint_mc_switch_power_open_close(pm::PMD.AbstractUnbalancedNFAModel, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int})
```

アクティブパワーのみモデルのための線形スイッチ電力オン/オフ制約。`relax`の場合、[インジケーター制約](https://jump.dev/JuMP.jl/stable/manual/constraints/#Indicator-constraints)が使用されます。

$$
\begin{align}
& P^{sw}_{i,c} \leq P^{swu}_{i,c} z^{sw}_i\ \forall i \in P,\forall c \in C \\
& P^{sw}_{i,c} \geq -P^{swu}_{i,c} z^{sw}_i\ \forall i \in P,\forall c \in C
\end{align}
$$
