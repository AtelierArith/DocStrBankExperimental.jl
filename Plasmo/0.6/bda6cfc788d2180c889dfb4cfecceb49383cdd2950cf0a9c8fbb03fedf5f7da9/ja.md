```
JuMP.add_variable(node::OptiNode, v::JuMP.AbstractVariable, name::String="")
```

変数 `v` をオプティノード `node` に追加します。この関数は `@variable` JuMP マクロの使用をサポートしています。オプションで、印刷用に変数に `base_name` を追加できます。
