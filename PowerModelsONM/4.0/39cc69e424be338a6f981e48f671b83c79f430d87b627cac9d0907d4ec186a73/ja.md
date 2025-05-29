```
objective_min_shed_load_traditional_rolling_horizon(pm::AbstractUnbalancedPowerModel)
```

ローリングホライズン問題のための最小ブロック負荷シェッド目的。これは、[`objective_min_shed_load_traditional`](@ref objective_min_shed_load_traditional)との違いは、目的の2行目のスイッチの合計がオプションではないことです。

$$
\begin{align*}
\mbox{minimize: } & \\
& \sum_{\substack{l \in L,t \in T}} W^{d}_{l,t} \left(1 - z^{d}_{l,t} \right) \\
& + \sum_{\substack{s \in S,t \in T}} \left[ W^{sw}_{s,t} \left(1 - \gamma_{s,t} \right )) +  W^{\Delta^{\gamma}}_{s,t}\Delta^{\gamma}_{s,t}\right ]\\
& + \sum_{\substack{e \in E,t \in T}} \epsilon^{ub}_{e} - \epsilon_{e,t} \\
& + \sum_{\substack{g \in G,t \in T}} f_1 P_{g,t} + f_0
\end{align*}
$$
