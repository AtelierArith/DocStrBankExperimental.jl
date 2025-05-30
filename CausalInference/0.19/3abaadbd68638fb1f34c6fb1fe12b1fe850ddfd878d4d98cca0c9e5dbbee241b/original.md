```
has_a_path(g::AbstractGraph, U::Vector, V::VectorOrVertex, exclude_vertices::AbstractVector = T[], nbs=Graphs.outneighbors)
```

Find if there is a (semi-directed) path connecting U with V not passing `exclude_vertices`, where `nbs=Graphs.outneighbors` determines the direction of traversal. 
