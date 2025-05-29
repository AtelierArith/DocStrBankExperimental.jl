```
checkroot!(net)
checkroot!(net::HybridNetwork, membership::Dict{Node, Int})
```

Set the root of `net` to an appropriate node and update the edges `containroot` field appropriately, using the `membership` output by [`treeedgecomponents`](@ref). A node is appropriate to serve as root if it belongs in the root tree-edge component, that is, the root of the tree-edge component graph.

  * If the current root is appropriate, it is left as is. The direction of edges (via `ischild1`) is also left as is, assuming it was in synch with the existing root.
  * Otherwise, the root is set to the first appropriate node in `net.node`, that is not a leaf. Then edges are directed away from this root.

A `RootMismatch` error is thrown if `net` is not a valid semidirected phylogenetic network (i.e. it is not possible to root the network in a way compatible with the given hybrid edges).

Output: the `membership` ID of the root component. The full set of nodes in the root component can be obtained as shown below. Warning: only use the output component ID after calling the second version `checkroot!(net, membership)`.

```jldoctest
julia> net = readnewick("(#H1:::0.1,#H2:::0.2,(((b)#H1)#H2,a));");

julia> membership = treeedgecomponents(net);

julia> rootcompID = checkroot!(net, membership);

julia> rootcomp = keys(filter(p -> p.second == rootcompID, membership));

julia> sort([n.number for n in rootcomp]) # number of nodes in the root component
3-element Vector{Int64}:
 -3
 -2
  4
```
