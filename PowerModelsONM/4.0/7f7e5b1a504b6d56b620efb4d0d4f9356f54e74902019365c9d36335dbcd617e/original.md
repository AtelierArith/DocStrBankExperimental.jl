```
constraint_mc_switch_power_open_close(pm::PMD.AbstractUnbalancedNFAModel, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int})
```

Linear switch power on/off constraint for Active Power Only Models. If `relax`, an [indicator constraint](https://jump.dev/JuMP.jl/stable/manual/constraints/#Indicator-constraints) is used.

$$
\begin{align}
& P^{sw}_{i,c} \leq P^{swu}_{i,c} z^{sw}_i\ \forall i \in P,\forall c \in C \\
& P^{sw}_{i,c} \geq -P^{swu}_{i,c} z^{sw}_i\ \forall i \in P,\forall c \in C
\end{align}
$$
