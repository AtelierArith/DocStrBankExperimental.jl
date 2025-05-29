```
num_edges(sim, ::Type{T}, [sum_ranks=true])
```

If `all_ranks` is `true` this function retrieves the number of edges of type `T` of the simulation `sim`. When it is set to `false`, the function will only return the number of edges of type `T` managed by the process.
