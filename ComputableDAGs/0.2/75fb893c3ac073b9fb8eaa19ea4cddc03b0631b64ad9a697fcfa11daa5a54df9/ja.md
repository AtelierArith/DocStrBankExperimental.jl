```
is_valid(graph::DAG, node::ComputeTaskNode)
```

与えられた計算ノードがグラフ内で有効であることを確認します。テストやデバッグ時には `@assert` または `@test` で呼び出してください。

これはまた [`is_valid_node(graph::DAG, node::Node)`](@ref) を呼び出します。
