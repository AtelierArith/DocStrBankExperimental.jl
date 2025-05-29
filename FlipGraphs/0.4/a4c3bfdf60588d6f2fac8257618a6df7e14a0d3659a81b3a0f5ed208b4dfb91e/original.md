```
struct FlipGraph <: AbstractGraph{Int}
```

A *graph* representing the **flip graph** of a **Δ-Complex**.

Vertices are isotopy classes of triangulations of the same surface.
Two vertices are linked by an edge, if the respective triangulations differ only by a single flip.
