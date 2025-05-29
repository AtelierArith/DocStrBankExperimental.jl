```
Bipartite{T <: Any} <: Partiteness{T}
```

A bipartite set of species is represented by two sets of species, called `top` and `bottom`. Both set of species are represented as `Vector{T}`, with a few specific constraints:

1. `T` cannot be a `Number` (*i.e.* nodes must have names, or be other objects)
2. All species in `top` must be unique
3. All species in `bottom` must be unique
4. No species can be found in both `bottom` and `top`
