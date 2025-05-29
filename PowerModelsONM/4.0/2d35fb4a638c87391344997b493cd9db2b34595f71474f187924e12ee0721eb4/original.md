```
constraint_disable_networking(pm::AbstractUnbalancedPowerModel, nw::Int; relax::Bool=false)
```

Constrains each microgrid to not network with another microgrid, while still allowing them to expand.

$$
\begin{align}
\sum_{k \in |{\cal L}|} y^k_{ab} = 1, \forall ab \in {\cal S}\\
y^k_{ab} - (1 - z_{ab}) \le x_k^{mg} \le  y^k_{ab} + (1 - z_{ab}), \forall k \in {\cal L}\\
y^{k'}_{dc} - (1 - z_{dc}) - (1 - z_{ab}) \le y^{k'}_{ab} \le  y^{k'}_{dc} + (1 - z_{dc}) + (1 - z_{ab}), \forall k \in {\cal L}, \forall ab \in {\cal T}_k, \forall dc \in {\cal T}_k\setminus {ab}
\end{align}
$$
