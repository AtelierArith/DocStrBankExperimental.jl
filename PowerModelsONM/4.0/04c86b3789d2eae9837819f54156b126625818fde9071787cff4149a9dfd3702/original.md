```
objective_mc_min_storage_utilization(pm::AbstractUnbalancedPowerModel)
```

Minimizes the amount of storage that gets utilized in favor of using all available generation first

$$
\begin{align*}
\mbox{minimize: } & \\
& \sum_{\substack{e \in E,t \in T}} \epsilon^{ub}_{e} - \epsilon_{e,t} \\
\end{align*}
$$
