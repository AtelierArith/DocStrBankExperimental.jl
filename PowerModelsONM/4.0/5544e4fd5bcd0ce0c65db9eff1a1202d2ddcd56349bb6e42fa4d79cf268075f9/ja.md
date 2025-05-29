```
constraint_mc_switch_state_voltage_open_closed(pm::PMD.AbstractUnbalancedACPModel, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int})
```

ACPU形式の線形スイッチの電源オン/オフ制約。

$$
\begin{align}
& |V^{fr}_{i,c}| - |V^{to}_{i,c}| \leq \left ( v^u_{i,c} - v^l_{i,c} \right ) \left ( 1 - z^{sw}_i \right )\ \forall i \in S,\forall c \in C \\
& |V^{fr}_{i,c}| - |V^{to}_{i,c}| \geq -\left ( v^u_{i,c} - v^l_{i,c} \right ) \left ( 1 - z^{sw}_i \right )\ \forall i \in S,\forall c \in C \\

\end{align}
$$
