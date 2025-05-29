```
attributes(node::Node) -> Dict{String,Union{String,Nothing}} | Nothing
```

ノードのすべての属性の `Dict` を返します。ノードが有効な要素ノードでない場合は `nothing` を返します。
