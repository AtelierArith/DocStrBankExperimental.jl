```
  length(c::Collection{T}, d::Pair...)
```

コレクション `c` の中で、`d` で指定された条件に一致するドキュメントの数をカウントします。

# 例

```julia-repl
julia> db = Polymake.Polydb.get_db();

julia> collection = db["Polytopes.Lattice.SmoothReflexive"];

julia> length(collection, "DIM"=>3, "N_FACETS"=>5)
4
```
