```
rem_edge!(g, e)
```

Remove an edge `e` from graph `g`. Return `true` if edge was removed successfully, otherwise return `false`.

### Implementation Notes

If `rem_edge!` returns `false`, the graph may be in an indeterminate state, as there are multiple points where the function can exit with `false`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> rem_edge!(g, 1, 2)
true

julia> rem_edge!(g, 1, 2)
false
```
