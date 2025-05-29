```
is_strongly_connected(g)
```

Return `true` if directed graph `g` is strongly connected.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_strongly_connected(g)
true
```
