```
constraint_switch_close_action_limit(pm::AbstractUnbalancedPowerModel, nw::Int)
```

Constraint for maximum allowed switch close actions in a single time step, as defined by `ref(pm, nw, :switch_close_actions_ub)`

$$
\begin{align}
\Delta^{\gamma}_i,~\forall i \in S & \\
s.t. & \\
& \Delta^{\gamma}_i \geq \gamma \left( 1 - \gamma_0 \right) \\
& \Delta^{\gamma}_i \geq -\gamma \left( 1 - \gamma_0 \right) \\
& \sum_{\substack{i \in S}} \Delta^{\gamma}_i \leq N_{\gamma=1}^{ub}
\end{align}
$$
