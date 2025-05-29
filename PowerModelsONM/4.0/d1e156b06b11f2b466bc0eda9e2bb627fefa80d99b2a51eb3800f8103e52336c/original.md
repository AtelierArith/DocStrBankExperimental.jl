```
objective_min_shed_load_traditional(pm::AbstractUnbalancedPowerModel)
```

Minimum block load shed objective for rolling horizon problem. Note that the difference between this and [`objective_min_shed_load_traditional_rolling_horizon`](@ref objective_min_shed_load_traditional_rolling_horizon) is that the sum over the switches in line 2 of the objective is optional, as determined by user inputs in the model, i.e., `enable_switch_state_open_cost` (default: false), and `disable-switch-state-change-cost` (default: false).

$$
\begin{align*}
\mbox{minimize: } & \\
& \sum_{\substack{l \in L,t \in T}} W^{d}_{l,t} \left(1 - z^{d}_{l,t} \right) \\
& + \sum_{\substack{s \in S,t \in T}} \left[ W^{sw}_{s,t} \left(1 - \gamma_{s,t} \right )) +  W^{\Delta^{\gamma}}_{s,t}\Delta^{\gamma}_{s,t}\right ]\\
& + \sum_{\substack{e \in E,t \in T}} \epsilon^{ub}_{e} - \epsilon_{e,t} \\
& + \sum_{\substack{g \in G,t \in T}} f_1 P_{g,t} + f_0
\end{align*}
$$
