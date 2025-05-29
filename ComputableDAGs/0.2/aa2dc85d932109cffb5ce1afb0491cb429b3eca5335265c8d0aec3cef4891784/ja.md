```
make_edge(n1::ComputeTaskNode, n2::DataTaskNode, index::Int)
```

`n1`（子）から `n2`（親）を指す新しい [`Edge`](@ref) を構築して返します。

index パラメータはデフォルトで 0 であり、親ノードの子の引数 index として渡されます。
