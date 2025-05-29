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

係数ベクトル `cref` に対して、点 `x` でのヤコビアン `J = dZ(x_i)/dc` を計算します。`vals` と `output` の説明については [`eval_graph`](@ref) を参照してください。
