```
add_node(
    graph::OptiGraph; label=Symbol(graph.label, Symbol(".n"), length(graph.optinodes)+1
)
```

`graph`に新しいオプティノードを追加します。デフォルトでは、ノードラベルは "n<i+1>" に設定されており、ここで "i" はグラフ内のノードの数です。
