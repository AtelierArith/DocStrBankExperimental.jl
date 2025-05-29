```
mutable struct EdgeMap{G <: AGraphOrDiGraph, T, D} <: AEdgeMap{T}
    g::G
    vtype::Type{T}
    data::D
end
```

Type implementing an edge map. The underlying container `data` can be a dictionary, a matrix or a vector (for graphs with indexed edges).

```
EdgeMap{T}(g, ::Type{T})
```

Returns a map that associates values of type `T` to the vertices of  graph `g`. The underlying storage structures is chosen accordingly.

```
EdgeMap(g, data)
```

Construct a EdgeMap with `data` as underlying storage. The storage type can be a matrix or an associative `edg => val` type or a vector for graph with indexed edges.

```
EdgeMap(g, f)
```

Construct an edge map with value `f(e)` for each `e` in `edges(g)`.
