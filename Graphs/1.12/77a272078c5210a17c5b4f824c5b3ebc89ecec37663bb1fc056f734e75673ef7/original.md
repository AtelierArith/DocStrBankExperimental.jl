```
is_weakly_connected(g)
```

Return `true` if the graph `g` is weakly connected. If `g` is undirected, this function is equivalent to [`is_connected(g)`](@ref).

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_weakly_connected(g)
true

julia> g = SimpleDiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> is_connected(g)
true

julia> is_strongly_connected(g)
false

julia> is_weakly_connected(g)
true
```
