```
isclockwise(vertices::AbstractMatrix{Float64}) -> Union{Bool,Nothing}
```

Return true/false if given vertices of a polygon in 2D space are placed clockwise/anticlockwise. Return nothing if the polygon is self-intersecting or some vertices are overlapped.  
