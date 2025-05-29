```
getdescnames(tree::AbstractTree, mrca::Int) :: Vector{String}
getdescnames(tree::AbstractTree) :: Vector{Vector{String}}
```

共通の祖先ノードからのすべての先端子孫の名前を見つけるか、または木のすべてのノードのそのような子孫名リストを取得します。
