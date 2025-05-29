```
path_length(ancestor::T, descendant::T)::Float64  where T<:AbstractNode
```

注意: この関数は、2つのノードの間に祖先関係があることを前提としています。

この関数は、祖先ノードと子孫ノードを分けるパスの長さを計算します。関数は、ノードの二進数表現を通じて指定されたパスに従います。
