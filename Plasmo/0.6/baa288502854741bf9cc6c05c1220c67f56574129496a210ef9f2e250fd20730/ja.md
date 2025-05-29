```
add_edge(
    graph::OptiGraph,
    nodes::OptiNode...;
    label=Symbol(graph.label, Symbol(".e"), length(graph.optiedges) + 1),
)
```

`graph`に`nodes`を接続する新しいoptiedgeを追加します。デフォルトでは、エッジラベルは"e<i+1>"に設定されており、ここで"i"はグラフ内のエッジの数です。
