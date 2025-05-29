```
PowerModelsGraph
    graph::Graphs.SimpleDiGraph
    node_comp_map::Dict{Int,Tuple{String, String}}
    edge_comp_map::Dict{Graphs.AbstractEdge,Tuple{String, String}}
    edge_connector_map::Dict{Graphs.AbstractEdge,Tuple{String, String}}
```

PowerModelsまたはPowerModelsDistributionネットワークのグラフを含む構造体で、4つのフィールドがあります：Graphs.SimpleDiGraph、ノードIDからコンポーネントへのマップ、エッジからコンポーネントへのマップ、およびエッジからコネクタへのマップ。
