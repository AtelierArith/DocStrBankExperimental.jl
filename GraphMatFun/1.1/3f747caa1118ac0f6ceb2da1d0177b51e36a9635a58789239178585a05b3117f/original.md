```
err=eval_runerr(
    graph,
    x;
    vals = nothing,
    relerrs = nothing,
    input = :A,
    output = size(graph.outputs, 1),
    mode = :bounds, # Can be :bounds, :rand, :estimate
    add_relerr = eps(),
)
```

Provides the running error of the graph evaluated in `x`. See [`eval_graph`](@ref) for meaning of `vals` and `output`. The kwarg `relerrs` is an anologous variable for the running error estimates in each node. The kwarg `mode` can be `:bounds`, `:rand`, `:estimate`, specifying if the code should make estimates or bounds, or random error within the bound.
