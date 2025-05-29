```
objective_min_shed_load_block_rolling_horizon(pm::AbstractUnbalancedPowerModel)
```

ローリングホライズン問題のための最小ブロック負荷シェッド目的。これは、目的の2行目におけるスイッチの合計がオプションでないという点で、[`objective_min_shed_load_block`](@ref objective_min_shed_load_block)とは異なることに注意してください。

```math \begin{align*} \mbox{minimize: } & 
& \sum*{\substack{b \in B,t \in T}} W^{bl}*{b,t} \left(1 - z^{bl}*{b,t} \right) 
& + \sum*{\substack{s \in S,t \in T}} \left[ W^{sw}*{s,t} \left(1 - \gamma*{s,t} \right )) +  W^{\Delta^{\gamma}}*{s,t}\Delta^{\gamma}*{s,t}\right ]
& + \sum*{\substack{e \in E,t \in T}} \epsilon^{ub}*{e} - \epsilon*{e,t} 
& + \sum*{\substack{g \in G,t \in T}} f*1 P*{g,t} + f_0 \end{align*}```
