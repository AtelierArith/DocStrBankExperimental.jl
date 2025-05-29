```
constraint_switch_close_action_limit(pm::AbstractUnbalancedPowerModel, nw_1::Int, nw_2::Int)
```

Constraint for maximum allowed switch close actions between time steps, as defined by `ref(pm, nw, :switch_close_actions_ub)`

$$
\begin{align}
\Delta^{\gamma}_i, ~\forall i \in S & \\
\gamma^{t}_i, ~\forall i \in S, ~\forall t \in T  & \\
\gamma^{t_1,t_2}_i, ~\forall i \in S, ~\forall (t_1,t_2) \in T  & \\
s.t.  & \\
& \gamma^{t_1,t_2}_i \geq 0 \\
& \gamma^{t_1,t_2}_i \geq \gamma^{t_2}_i + \gamma^{t_1}_i - 1 \\
& \gamma^{t_1,t_2}_i \leq \gamma{t_1}_i \\
& \gamma^{t_1,t_2}_i \leq \gamma{t_2}_i \\
& \Delta^{\gamma}_i \geq \gamma^{t_2}+i - \gamma^{t_1,t_2}_i \\
& \Delta^{\gamma}_i \geq \gamma^{t_2}+i + \gamma^{t_1,t_2}_i \\
& \sum_{\substack{i \in S}} \Delta^{\gamma}_i \leq N_{\gamma=1}^{ub}
\end{align}
$$
