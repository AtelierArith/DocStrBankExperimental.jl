```
insert_node!(graph::DAG, node::Node)
insert_node!(graph::DAG, task::AbstractTask, name::String="")
```

グラフにノードを挿入するか、または与えられたタスクからノードを構築して挿入します。
