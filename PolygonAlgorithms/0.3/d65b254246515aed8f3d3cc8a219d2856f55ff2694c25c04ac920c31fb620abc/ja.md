```
intersect_edges(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D})
```

`polygon1` と `polygon2` によって与えられた頂点のエッジの交差点にあるすべての点を見つけます。

時間計算量は `O(nm)` であり、ここで `n` と `m` はそれぞれポリゴン 1 と 2 の頂点の数です。
