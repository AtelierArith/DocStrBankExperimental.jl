```
objective_min_shed_load_block(pm::AbstractUnbalancedPowerModel)
```

ローリングホライズン問題における最小ブロック負荷シェッド目的。これは、[`objective_min_shed_load_block_rolling_horizon`](@ref objective_min_shed_load_block_rolling_horizon)との違いは、目的の2行目におけるスイッチの合計がオプションであり、モデル内のユーザー入力によって決定されることです。すなわち、`enable_switch_state_open_cost`（デフォルト：false）および`disable-switch-state-change-cost`（デフォルト：false）です。

```math \begin{align*} \mbox{minimize: } & 
& \sum*{\substack{b \in B,t \in T}} W^{bl}*{b,t} \left(1 - z^{bl}*{b,t} \right) 
& + \sum*{\substack{s \in S,t \in T}} \left[ W^{sw}*{s,t} \left(1 - \gamma*{s,t} \right )) +  W^{\Delta^{\gamma}}*{s,t}\Delta^{\gamma}*{s,t}\right ]
& + \sum*{\substack{e \in E,t \in T}} \epsilon^{ub}*{e} - \epsilon*{e,t} 
& + \sum*{\substack{g \in G,t \in T}} f*1 P*{g,t} + f_0 \end{align*}```
