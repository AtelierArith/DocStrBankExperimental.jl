```
function node_age(node<:AbstractNode)::Float64
```

ノードの年齢を計算します。木がウルトラメトリックであれば、ノードの年齢はノードの高さと同じです。これは、ノードと根の間の経路の長さを根の高さから引くことによって計算されます。これは、根から最も遠い葉のノード年齢が0であり、根ノードが「最も古い」ノードであると仮定した場合のノードの年齢を表します。
