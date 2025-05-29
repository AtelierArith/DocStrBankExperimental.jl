```
overlap(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: UnipartiteNetwork}
```

Returns the overlap graph for a unipartite network. The `dims` keyword argument can be `1` (overlap based on preys) or `2` (overlap based on predators), or `nothing` (default; overlap based on both predators and preys). The overlap is returned as a vector of named tuples, with elements `pair` (a tuple of species names), and `overlap` (the number of shared interactors). The ordering within the pair of species is unimportant, since overlap graphs are symetrical.
