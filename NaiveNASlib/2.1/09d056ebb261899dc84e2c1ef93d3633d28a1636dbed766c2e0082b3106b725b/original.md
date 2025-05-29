```
vertices(g::CompGraph)
```

Return an topologically sorted array of all vertices in the graph `g`.

# Examples

```julia-repl
julia> ins = InputVertex.(1:2);

julia> v1 = CompVertex(+, ins...);

julia> v2 = CompVertex(*, v1, ins[2]);

julia> graph = CompGraph(ins, v2);

julia> vertices(graph)
4-element Array{AbstractVertex,1}:
 InputVertex(1)
 InputVertex(2)
 CompVertex(+), inputs=[InputVertex(1), InputVertex(2)]
 CompVertex(*), inputs=[CompVertex(+), InputVertex(2)]
```
