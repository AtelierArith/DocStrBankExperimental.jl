```julia
graph_agents(
    n::Int64;
    node,
    graph_mort_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.GraphAgent{EasyABM.StaticType, EasyABM.StaticType}}

```

nのプロパティを指定されたキーワード引数として持つグラフエージェントのリストを作成します。
