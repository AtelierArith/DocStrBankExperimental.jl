```
is_scheduled(graph::DAG)
```

Validate that the entire graph has been scheduled, i.e., every [`ComputeTaskNode`](@ref) has its `.device` set.
