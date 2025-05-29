```julia
struct FunctionLayer{__T_nodes, __T_skip} <: LuxCore.AbstractLuxWrapperLayer{:nodes}
```

複数の [`DecisionNodes`](@ref) のコンテナです。ノードのすべての出力を蓄積します。

# フィールド

  * `nodes`
  * `skip`
