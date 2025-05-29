```
(order,can_be_deallocated,max_nodes)=get_topo_order(
    graph;
    priohelp = Dict{Symbol,Float64}(),
    free_mem_bonus = 1000,
    will_not_dealloc = [:I],
    input = :A,
)
```

Computes a topological sort of `graph`, that is, an ordering of the nodes following which the function the graph represents can be evaluated. The `priohelp` kwarg can be used to obtain a different topological ordering by changing the node priority. The code assumes that the nodes `:I` and `input` do not need to be computed.

The code uses a heuristic to minimize pathwidth. It is based on a point system. You can influence the computation order by providing a `priohelp`. If you want node `:B4` to be computed earlier, you can set `priohelp[:B4]=-5000.0`. The `free_mem_bonus` is used in the heuristic to prioritize the computation of nodes which release other nodes. The vector `will_not_deallocate` influences the order specifying nodes that will not be deallocated and therefore gets no `free_mem_bonus`.

The return value `order` is a `Vector` of Symbols, and `can_be_deallocated` is a `Vector{Vector{Symbol}}` where the element `i` specifies the `Symbols` that are unused after step `i` in the ordering. The `max_nodes` is the pathwidth.
