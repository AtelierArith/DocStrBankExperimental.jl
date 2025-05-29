```
variable_mc_storage_power_mi_on_off(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    bounded::Bool=true,
    report::Bool=true
)
```

ストレージの変数、*ストレージインジケーター* $z^{strg}_i$ 変数を省略：

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

, $d^{on}_i$ は `relax=false` の場合はバイナリになります。変数は `report=true` の場合に解に現れます。
