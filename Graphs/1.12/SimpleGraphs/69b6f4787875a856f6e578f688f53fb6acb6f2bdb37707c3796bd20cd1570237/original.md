```
squash(g::Union{SimpleGraph, SimpleDiGraph}; alwayscopy=true)
```

Specialised version of `Graphs.squash` for `SimpleGraph` and `SimpleDiGraph`. If `alwayscopy` is `true`, the resulting graph will always be a copy, otherwise it can also be the original graph.
