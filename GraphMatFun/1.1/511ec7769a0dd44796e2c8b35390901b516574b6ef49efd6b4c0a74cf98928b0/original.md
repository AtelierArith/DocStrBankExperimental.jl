```
result=eval_graph(
    graph,
    x;
    vals = nothing,
    input = :A,
    output = size(graph.outputs, 1),
    comporder = nothing,
)
```

Evaluates a graph in the value `x` which is typically a scalar value or a matrix. If `x` is a Vector, the values will be evaluated elementwise.

The `comporder` is a `Vector` of nodes specifying in which order the graph should be computed. By default [`get_topo_order`](@ref) is used.

The `output` is an `Int` specifying which node should be considered as output. The output node is `graph.outputs[output]`.

The `vals` is used to inspect contents other than the output inside the graph. Typically `vals` is a `Dict`. It will be modified to contain the computed nodes of the graph. If we wish to inspect node `X3`, we can initiate an empty dict as input:

```julia-repl
julia > vals = Dict{Symbol,Any}();
julia > eval_graph(graph, A, vals = vals);
julia > vals[:X3]
```
