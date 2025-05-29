```
JuMP.set_optimizer(
    graph::OptiGraph, 
    JuMP.@nospecialize(optimizer_constructor); 
    add_bridges::Bool=true
)
```

`graph`に`optimizer_constructor`を渡してオプティマイザを設定します。
