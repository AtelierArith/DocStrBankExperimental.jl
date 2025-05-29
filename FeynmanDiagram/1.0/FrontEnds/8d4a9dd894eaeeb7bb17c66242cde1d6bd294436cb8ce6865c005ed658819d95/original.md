```
function leafstates(leaf_maps::Vector{Dict{Int,G}}, maxloopNum::Int)

Extracts leaf information from the leaf mapping from the leaf value's index to the leaf node for all graph partitions. 
The information includes their initial value, type, orders, in/out time, and loop momentum index.
The loop basis is also obtained for all the graphs.
```

# Arguments:

  * `leaf_maps`: A vector of the dictionary mapping the leaf value's index to the Graph of this leaf.               Each dict corresponds to a graph partition, such as (order, Gorder, Vorder).
  * `maxloopNum`: The maximum loop-momentum number.

# Returns

  * A tuple of vectors containing information about the leaves of graphs, including their initial values, types, orders, input and output time indexes, and loop-momenta indexes.
  * Loop-momentum basis (`::Vector{Vector{Float64}}`) for all the graphs.
