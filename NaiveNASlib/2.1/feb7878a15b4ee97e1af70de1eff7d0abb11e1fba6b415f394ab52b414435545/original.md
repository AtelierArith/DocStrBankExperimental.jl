```
remove!(v::MutationVertex, strategy=RemoveStrategy())
```

Removes `v` from the graph by removing it from its [`inputs`](@ref) and [`outputs`](@ref).

It is possible to supply a strategy for how to 1) reconnect the inputs and outputs of `v` and 2) align the input and output sizes of the `inputs` and `outputs` of `v`.

Default strategy is to first set `nin==nout` for `v` and then connect all its  [`inputs`](@ref) to all its [`outputs`](@ref).
