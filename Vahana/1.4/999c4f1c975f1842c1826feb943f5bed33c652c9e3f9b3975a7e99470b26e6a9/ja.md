```
add_agents!(sim, agents)::Vector{AgentID}
```

シミュレーション `sim` に複数のエージェントを一度に追加します。

`agents` はエージェントの任意の反復可能なセット、または任意の数のエージェントを引数として取ることができます。

エージェントのタイプは、[`register_agenttype!`](@ref) を呼び出すことで事前に登録されている必要があります。

`add_agents!` は AgentIDs のベクターを返します。これは、[`finish_init!`](@ref) が呼び出される前（`add_agents!` が初期化フェーズで呼び出された場合）や、遷移関数が終了する前（`add_agents!` が [`apply!`](@ref) コールバックで呼び出された場合）に、このエージェントからまたはこのエージェントへのエッジを作成するために使用できます。IDを他の目的で使用しないでください。安定性は保証されていません。

他にも [`add_agent!`](@ref)、[`register_agenttype!`](@ref)、[`add_edge!`](@ref)、および [`add_edges!`](@ref) を参照してください。
