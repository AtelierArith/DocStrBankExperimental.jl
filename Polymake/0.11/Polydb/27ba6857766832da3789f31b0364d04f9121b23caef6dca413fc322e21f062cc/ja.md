```
  length(c::Collection{T}, d::Dict=Dict())
```

コレクション `c` の中で、`d` で与えられた条件に一致するドキュメントの数をカウントします。

# 例

```julia-repl
julia> db = Polymake.Polydb.get_db();

julia> collection = db["Polytopes.Lattice.SmoothReflexive"];

julia> query = Dict("DIM"=>3, "N_FACETS"=>5);

julia> length(collection, query)
4
```
