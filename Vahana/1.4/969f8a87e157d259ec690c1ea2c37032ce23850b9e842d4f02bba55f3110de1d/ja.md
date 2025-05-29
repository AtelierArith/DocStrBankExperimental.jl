```
all_agents(sim, ::Type{T}, [all_ranks=true])
```

この関数は、シミュレーション `sim` のタイプ T のすべてのエージェントの状態のベクトルを取得します。

`all_ranks` 引数は、すべてのランクのエージェントを含めるか、並列シミュレーションで現在のランクのエージェントのみを含めるかを決定します。`all_ranks` が `true` の場合、関数はすべてのランクにわたるすべてのエージェント識別子のベクトルを返します。

`all_agents` と [`all_agentids`](@ref) によって返されるエージェントの状態と ID は同じ順序です。

!!! info
    `all_agents` は、引数 `all_ranks` が true に設定されている場合、遷移関数内で呼び出すことはできません。


関連情報としては、[`all_agentids`](@ref)、[`add_agents!`](@ref)、および [`num_agents`](@ref) があります。
