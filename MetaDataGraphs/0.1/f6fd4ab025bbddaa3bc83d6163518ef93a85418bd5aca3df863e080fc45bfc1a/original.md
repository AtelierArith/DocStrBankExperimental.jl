```
AbstractDataGraph{T,VL,VD,ED,GD} <: AbstractGraph{T}
```

General template for graphs with metadata.

  * `T<:Integer` is the type of vertices
  * `VL` is the type of vertex labels (cannot be a subtype of `Integer`)
  * `VD` is the type of vertex data objects
  * `ED` is the type of edge data objects
  * `GD` is the type of the graph data object
