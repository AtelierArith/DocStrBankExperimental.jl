```
is_matching(graph::SimpleGraph, config)
```

Returns true if `config` is a valid matching on `graph`, and `false` if a vertex is double matched. `config` is a vector of boolean variables, which has one to one correspondence with `edges(graph)`.
