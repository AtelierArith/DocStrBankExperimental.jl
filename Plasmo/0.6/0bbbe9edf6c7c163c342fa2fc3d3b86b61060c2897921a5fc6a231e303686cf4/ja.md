```
JuMP.add_constraint(node::OptiNode, con::JuMP.AbstractConstraint, name::String="")
```

オプティノード `node` に制約 `con` を追加します。この関数は @constraint JuMP マクロの使用をサポートしています。
