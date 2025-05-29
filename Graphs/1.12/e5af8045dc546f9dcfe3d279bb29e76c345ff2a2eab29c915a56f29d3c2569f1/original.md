```
sum(g)
```

Return the number of edges in `g`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> sum(g)
2
```
