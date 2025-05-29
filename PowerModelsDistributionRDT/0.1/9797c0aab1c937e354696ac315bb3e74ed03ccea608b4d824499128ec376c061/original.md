```
constraint_mc_switch_power_open_close(
    pm::AbstractUnbalancedPowerModel,
    nw::Int,
    i::Int,
    f_bus::Int,
    t_bus::Int,
    f_connections::Vector{Int},
    t_connections::Vector{Int}
)
```

generic switch power open/closed constraint

$$
\begin{align}
& S^{sw}_{i,c} \leq S^{swu}_{i,c} z^{sw}_i\ \forall i \in S,\forall c \in C \\
& S^{sw}_{i,c} \geq -S^{swu}_{i,c} z^{sw}_i\ \forall i \in S,\forall c \in C
\end{align}
$$
