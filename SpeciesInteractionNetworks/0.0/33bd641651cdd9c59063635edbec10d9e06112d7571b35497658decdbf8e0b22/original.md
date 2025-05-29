```
Unipartite{T <: Any} <: Partiteness{T}
```

A unipartite set of species is represented by a single set of species, called `margin` internally. Both set of species are represented as `Vector{T}`, with a few specific constraints:

1. `T` cannot be a `Number` (*i.e.* nodes must have names, or be other objects)
2. All species in `margin` must be unique
