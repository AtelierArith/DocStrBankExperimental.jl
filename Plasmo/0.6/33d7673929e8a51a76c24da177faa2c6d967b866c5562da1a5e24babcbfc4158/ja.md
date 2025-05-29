```
all_edges(graph::OptiGraph)::Vector{<:OptiNode}
```

`graph`の各サブグラフをトラバースすることによって、すべてのoptiedgesを再帰的に収集します。
