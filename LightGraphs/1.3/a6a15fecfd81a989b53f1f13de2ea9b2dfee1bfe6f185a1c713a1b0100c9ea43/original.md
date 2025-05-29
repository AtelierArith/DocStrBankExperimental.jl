```
is_connected(g)
```

Return `true` if graph `g` is connected. For directed graphs, return `true` if graph `g` is weakly connected.

# Examples

```jldoctest
julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> is_connected(g)
true

julia> g = SimpleGraph([0 1 0 0 0; 1 0 1 0 0; 0 1 0 0 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> is_connected(g)
false

julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_connected(g)
true
```
