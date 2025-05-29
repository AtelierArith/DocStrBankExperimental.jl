```
add_graph!(sim::Simulation, graph, agent_constructor, edge_constructor) -> Vector{AgentID}
```

`sim`にGraphs.jlパッケージからの`graph`を追加し、`graph`のすべての頂点を新しいエージェントとして含めます。

`graph`はGraphs.GraphまたはGraphs.DiGraphでなければなりません。

`graph`の各頂点に対して、`agent_constructor`関数が呼び出され、Graphs.vertixが引数として渡されます。`graph`の各エッジに対して、`edge_constructor`関数が呼び出され、Graphs.edgeが引数として渡されます。

`agent_constructor`によって作成されたエージェントのエージェントタイプは、すでに[`register_agenttype!`](@ref)を介して登録されている必要があり、エッジタイプについても[`register_edgetype!`](@ref)を介して登録されている必要があります。

!!! info
    add_graph!は、モデル実装によってGraphs.jlパッケージがインポートされている場合にのみ利用可能です。


作成されたエージェントのIDを含むベクターを返します。
