```
objective_mc_min_storage_utilization(pm::AbstractUnbalancedPowerModel)
```

利用可能な発電を優先して、使用されるストレージの量を最小化します。

$$
\begin{align*}
\mbox{minimize: } & \\
& \sum_{\substack{e \in E,t \in T}} \epsilon^{ub}_{e} - \epsilon_{e,t} \\
\end{align*}
$$
