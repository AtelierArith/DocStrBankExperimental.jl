```
intersect_edges(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D})
```

Find all points which lie on the intersection of the edges of the vertices given by `polygon1` and `polygon2`.

Time complexity is `O(nm)` where `n` and `m` are the number of vertices of polygon 1 and 2 respectively.
