```
JuMP.set_optimizer(
    node::OptiNode, 
    JuMP.@nospecialize(optimizer_constructor); 
    add_bridges::Bool=true
)
```

オプティノードのための最適化器を設定します。これは内部的にノードを最適化するために使用される新しいオプティグラフを作成します。このメソッドをノードで呼び出すと、新しく作成されたグラフが返されます。
