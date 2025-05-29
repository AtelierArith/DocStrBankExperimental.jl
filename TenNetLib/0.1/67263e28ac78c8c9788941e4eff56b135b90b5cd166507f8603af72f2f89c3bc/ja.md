```
function find_sum_central_node(graph::Graph{T}) where T
function find_sum_central_node(graph::Graph{T}, nodes::Set{T}) where T
function find_sum_central_node(graph::Graph{T}, nodes::Vector{T}) where T
```

`Graph`の合計中心ノードを見つけます。オプションで、`nodes`が指定されている場合は、`nodes`に関して中心ノードを見つけます。
