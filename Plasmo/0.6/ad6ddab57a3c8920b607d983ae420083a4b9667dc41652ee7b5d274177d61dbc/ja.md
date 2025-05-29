```
all_nodes(graph::OptiGraph)::Vector{<:OptiNode}
```

`graph`の各サブグラフをトラバースすることによって、すべてのオプティノードを再帰的に収集します。
