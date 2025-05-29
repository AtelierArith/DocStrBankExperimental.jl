```
constraint_grid_forming_inverter_per_cc_traditional(pm::AbstractUnbalancedPowerModel, nw::Int; relax::Bool=false)
```

グラフの各接続コンポーネントが、コンポーネントが有効な場合にのみ1つのグリッド形成インバータを持つように制約します。

$$
\begin{align}
& \sum_{k \in {\cal B}} y^k_{ab} \le z^{sw}_{ab} &\forall ab \in {\cal E}_{sw} \\
& \sum_{ab \in {\cal T}_k} (1-z^{sw}_{ab}) - |{\cal T}_k| + 1 \le \sum_{i \in {\cal D}_k} z^{inv}_i \le 1 & \forall k \in {\cal B} \\
& S^g_i \le \overline{S}^g_i (\sum_{ab \in {\cal T}_k} z^{sw}_{ab} + \sum_{j \in {\cal D}_k} z^{inv}_j) & \forall i \in {\cal G} \\
& S^g_i \le \overline{S}^g_i (\sum_{ab \in {\cal T}_k} \sum_{k \in {\cal B}} y_{ab}^k + \sum_{j \in {\cal D}_k} z^{sw}_j) & \forall i \in {\cal G} \\
& S^g_i \ge \underline{S}^g_i (\sum_{ab \in {\cal T}_k} z^{sw}_{ab} + \sum_{j \in {\cal D}_k} z^{inv}_j) & \forall i \in {\cal G} \\
& S^g_i \ge \underline{S}^g_i (\sum_{ab \in {\cal T}_k} \sum_{k \in {\cal B}} y_{ab}^k + \sum_{j \in {\cal D}_k} z^{sw}_j) & \forall i \in {\cal G} \\
& y^k_{ab} - (1 - z^{sw}_{ab}) \le \sum_{i \in {\cal D}_k} z^{inv}_i \le  y^k_{ab} + (1 - z^{sw}_{ab}) & \forall k \in {\cal B},\forall ab \in {\cal E}_{sw} \\
& y^{k'}_{dc} - (1 - z^{sw}_{dc}) - (1 - z^{sw}_{ab}) \le y^{k'}_{ab} \le  y^{k'}_{dc} + (1 - z^{sw}_{dc}) + (1 - z^{sw}_{ab}) \\
& ~~~~ \forall k \in {\cal B},\forall k' \in {\cal B}/{k},\forall ab \in {\cal E}_{sw},\forall dc \in {\cal E}_{sw}/{ab} \nonumber \\
& y_{ab}^k \le \sum_{i \in {\cal D}_k} z^{inv}_i & \forall k \in {\cal B},\forall ab \in {\cal E}_{sw} \\
& -z^{sw}_{ab} |{\cal B}| \le f_{ab}^k \le z^{sw}_{ab} |{\cal B}| & \forall k \in {\cal B},\forall ab \in {\cal E}_{sw} \\
& 0 \le \xi_{ab}^k \le 1 & \forall k \in {\cal B},\forall ab \in {\cal E}_{sw} \\
& \sum_{ab \in {\cal T}_k : a = k} f_{ab}^k - \sum_{ab \in {\cal T}_k : b = k} f_{ab}^k + \sum_{ab \in {\cal E}_v^k} \xi_{ab}^k = |{\cal B}| - 1 & \forall k \in {\cal B} \\
& \sum_{ab \in {\cal T}_{k'} : a = k'} f_{ab}^k - \sum_{ab \in {\cal T}_{k'} : b = k'} f_{ab}^k  -  \xi_{kk'}^k = -1, \;\;\; \forall k' \ne k & \forall k \in {\cal B} \\
& y_{ab}^k \le 1 - \xi_{kk'}^k & \forall k' \ne k, ab \in {\cal T}_{k'} \\
\end{align}
$$
