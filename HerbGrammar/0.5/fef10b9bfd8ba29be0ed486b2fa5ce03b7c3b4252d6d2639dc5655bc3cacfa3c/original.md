```
mindepth(grammar::AbstractGrammar, typ::Symbol, dmap::AbstractVector{Int})
```

Returns the minimum depth achievable for a given nonterminal symbol. The minimum depth is the depth of the lowest tree that can be made using `typ`  as a start symbol. `dmap` can be obtained from [`mindepth_map`](@ref).
