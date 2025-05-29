```
J=eval_jac(
    graph,
    x,
    cref;
    vals = nothing,
    input = :A,
    output = size(graph.outputs, 1),
)
```

Computes Jacobian `J = dZ(x_i)/dc`, with respect to the coefficients given in the vector `cref`, and points in `x`. See [`eval_graph`](@ref) for description of `vals` and `output`.
