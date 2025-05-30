```
AbstractSubdomain
```

2つの [`PB.Domain`](@ref) の間の関係を定義し、1つのドメインのインデックスを他のドメインの関連インデックスにマッピングします。例えば、境界に隣接する内部セルです。

具体的なサブタイプは以下を実装する必要があります：

[`subdomain_view`](@ref)

[`subdomain_indices`](@ref)
