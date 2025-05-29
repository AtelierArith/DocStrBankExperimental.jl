```
find_longest_path(graph_result::BioGraph.GraphResult, optimizer_factory; is_weighted::Bool, source_node::Int64, sink_node::Int64, has_path::String)
```

グラフ内の最長パスを見つけます。入力:

  * `GraphResult`
  * `CPLEX.Optimizer`のようなJuMPオプティマイザーファクトリ
  * `has_path`: 最長パスに含まれる必要があるパスを示すオプションの文字列。
  * `is_weighted`: `true`の場合、重み付きの最短パスを見つけます。
  * `source_node`, `sink_node`: ソースノードとシンクノードを持つ最長パスを見つけます。
