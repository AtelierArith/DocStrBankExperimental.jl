```
make_edge(n1::DataTaskNode, n2::ComputeTaskNode)
```

`n1`（子）から `n2`（親）を指す新しい [`Edge`](@ref) を構築して返します。

インデックスパラメータはデフォルトで 0 であり、親ノードにその子の引数インデックスとして渡されます。
