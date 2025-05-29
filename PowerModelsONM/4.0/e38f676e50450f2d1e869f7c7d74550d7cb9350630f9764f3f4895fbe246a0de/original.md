```
objective_min_shed_load_block(pm::AbstractUnbalancedPowerModel)
```

Minimum block load shed objective for rolling horizon problem. Note that the difference between this and [`objective_min_shed_load_block_rolling_horizon`](@ref objective_min_shed_load_block_rolling_horizon) is that the sum over the switches in line 2 of the objective is optional, as determined by user inputs in the model, i.e., `enable_switch_state_open_cost` (default: false), and `disable-switch-state-change-cost` (default: false).

```math \begin{align*} \mbox{minimize: } & \
& \sum*{\substack{b \in B,t \in T}} W^{bl}*{b,t} \left(1 - z^{bl}*{b,t} \right) \
& + \sum*{\substack{s \in S,t \in T}} \left[ W^{sw}*{s,t} \left(1 - \gamma*{s,t} \right )) +  W^{\Delta^{\gamma}}*{s,t}\Delta^{\gamma}*{s,t}\right ]\
& + \sum*{\substack{e \in E,t \in T}} \epsilon^{ub}*{e} - \epsilon*{e,t} \
& + \sum*{\substack{g \in G,t \in T}} f*1 P*{g,t} + f_0 \end{align*}```
