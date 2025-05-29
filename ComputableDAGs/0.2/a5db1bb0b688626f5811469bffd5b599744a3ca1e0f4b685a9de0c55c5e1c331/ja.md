```
graph(problem_instance)
```

与えられた `problem_instance` の [`DAG`](@ref) を生成します。グラフのすべてのエントリノード（[`get_entry_nodes`](@ref] を参照）には、名前が設定されている必要があります。これらの名前のそれぞれに対して有効な式を返すために [`input_expr`](@ref) を実装してください。

`problem_instance` に関する詳細は、ドキュメントを参照してください。
