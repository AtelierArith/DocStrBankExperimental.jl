```
variable_mc_storage_power_mi_on_off(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    bounded::Bool=true,
    report::Bool=true
)
```

Variables for storage, *omitting* the storage indicator $z^{strg}_i$ variable:

$$
\begin{align}
p^{strg}_i,~\forall i \in S \\
q^{strg}_i,~\forall i \in S \\
q^{sc}_{i},~\forall i \in S \\
\epsilon_i,~\forall i \in S \\
c^{strg}_i,~\forall i \in S \\
c^{on}_i \in {0,1},~\forall i \in S \\
d^{on}_i \in {0,1},~\forall i \in S \\
\end{align}
$$

$$
c^{on}_i
$$

, $d^{on}_i$ will be binary if `relax=false`. Variables will appear in solution if `report=true`.
