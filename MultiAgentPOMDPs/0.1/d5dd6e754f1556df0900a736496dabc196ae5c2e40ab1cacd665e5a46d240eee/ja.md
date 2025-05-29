```
function coordination_graph(m::JointMDP)
function coordination_graph(m::JointMDP, s::S) where S
```

コーディネーショングラフのための LightGraphs.SimpleGraph（または適切な構造）を返します。
