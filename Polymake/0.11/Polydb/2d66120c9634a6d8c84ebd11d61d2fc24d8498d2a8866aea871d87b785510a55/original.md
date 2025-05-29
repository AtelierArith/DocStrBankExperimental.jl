```
  length(c::Collection{T}, d::Pair...)
```

Count documents in a collection `c` matching the criteria given by `d`.

# Examples

```julia-repl
julia> db = Polymake.Polydb.get_db();

julia> collection = db["Polytopes.Lattice.SmoothReflexive"];

julia> length(collection, "DIM"=>3, "N_FACETS"=>5)
4
```
