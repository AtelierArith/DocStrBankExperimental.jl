```
apply_edges(fmsg, g; [xi, xj, e])
apply_edges(fmsg, g, xi, xj, e=nothing)
```

Returns the message from node `j` to node `i` applying the message function `fmsg` on the edges in graph `g`. In the message-passing scheme, the incoming messages  from the neighborhood of `i` will later be aggregated in order to update the features of node `i` (see [`aggregate_neighbors`](@ref)).

The function `fmsg` operates on batches of edges, therefore `xi`, `xj`, and `e` are tensors whose last dimension is the batch size, or can be named tuples of  such tensors.

# Arguments

  * `g`: An `AbstractGNNGraph`.
  * `xi`: An array or a named tuple containing arrays whose last dimension's size        is `g.num_nodes`. It will be appropriately materialized on the       target node of each edge (see also [`edge_index`](@ref GNNGraphs.edge_index)).
  * `xj`: As `xi`, but now to be materialized on each edge's source node.
  * `e`: An array or a named tuple containing arrays whose last dimension's size is `g.num_edges`.
  * `fmsg`: A function that takes as inputs the edge-materialized `xi`, `xj`, and `e`.      These are arrays (or named tuples of arrays) whose last dimension' size is the size of      a batch of edges. The output of `f` has to be an array (or a named tuple of arrays)      with the same batch size. If also `layer` is passed to propagate,     the signature of `fmsg` has to be `fmsg(layer, xi, xj, e)`      instead of `fmsg(xi, xj, e)`.

See also [`propagate`](@ref) and [`aggregate_neighbors`](@ref).
