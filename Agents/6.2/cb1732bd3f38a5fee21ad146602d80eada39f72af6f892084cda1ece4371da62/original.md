```
rem_vertex!(model::ABM{<:GraphSpace}, n::Int)
```

Remove node (i.e. position) `n` from the model's graph. All agents in that node are removed from the model.

**Warning:** Graphs.jl (and thus Agents.jl) swaps the index of the last node with that of the one to be removed, while every other node remains as is. This means that when doing `rem_vertex!(n, model)` the last node becomes the `n`-th node while the previous `n`-th node (and all its edges and agents) are deleted.
