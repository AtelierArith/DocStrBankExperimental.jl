```
constraint_mc_switch_voltage_open_close(pm::PMD.LPUBFDiagModel, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int})
```

LPUBFDiagModelのための線形スイッチ電源オン/オフ制約。

$$
\begin{align}
& w^{fr}_{i,c} - w^{to}_{i,c} \leq \left ( v^u_{i,c} \right )^2 \left ( 1 - z^{sw}_i \right )\ \forall i \in S,\forall c \in C \\
& w^{fr}_{i,c} - w^{to}_{i,c} \geq -\left ( v^u_{i,c}\right )^2 \left ( 1 - z^{sw}_i \right )\ \forall i \in S,\forall c \in C
\end{align}
$$
