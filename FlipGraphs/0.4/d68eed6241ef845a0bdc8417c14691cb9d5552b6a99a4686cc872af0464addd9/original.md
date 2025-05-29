```
struct FlipGraphPlanar <: AbstractGraph{Int32}
```

A Graph representing the **flip graph** of a **convex polygon**. 

Vertices are different triangulations of the same convex polygon. Two vertices are linked by an edge, if the respective graphs differ only by a single flip.
