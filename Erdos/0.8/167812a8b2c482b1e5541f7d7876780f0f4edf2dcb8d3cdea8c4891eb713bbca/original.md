```
struct ConstVertexMap{T} <: AVertexMap{T}
    val::T
end
```

A type representing a constant vector map. Any attempt to change the internal value, e.g. `vm[1] = 4`, will fail silently.
