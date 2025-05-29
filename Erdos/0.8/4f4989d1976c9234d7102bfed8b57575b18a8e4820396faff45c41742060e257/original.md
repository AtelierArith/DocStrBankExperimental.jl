```
mutable struct VertexMap{G <: AGraphOrDiGraph, T, D} <: AVertexMap{T}
    g::G
    vtype::Type{T}
    data::D
end
```

Type implementing a vertex map. The underlying container `data` can be a dictionary or a vector.

```
VertexMap{T}(g, ::Type{T})
```

Returns a map that associates values of type `T` to the vertices of  graph `g`.  The underlying storage structures is chosen accordingly.

```
VertexMap(g, data)
```

Construct a VertexMap with `data` as underlying storage.

```
VertexMap(g, f)
```

Construct a vertex map with value `f(u)` for `u in 1:nv(g)`.
