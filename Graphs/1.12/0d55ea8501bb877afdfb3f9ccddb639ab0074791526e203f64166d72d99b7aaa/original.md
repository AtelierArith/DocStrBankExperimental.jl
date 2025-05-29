```
sum(g, i)
```

Return a vector of indegree (`i`=1) or outdegree (`i`=2) values for graph `g`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> sum(g, 2)
5-element Vector{Int64}:
 1
 1
 2
 1
 1

julia> sum(g, 1)
5-element Vector{Int64}:
 1
 1
 1
 2
 1
```
