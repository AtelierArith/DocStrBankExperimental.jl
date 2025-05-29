```
function leafstates(leaf_maps::Vector{Dict{Int,G}}, labelProd::LabelProduct) where {G<:Union{Graph,FeynmanGraph}}

Extracts leaf information from the leaf mapping from the leaf value's index to the leaf node for all graph partitions
and their associated LabelProduct data (`labelProd`). 
The information includes their initial value, type, orders, in/out time, and loop momenta.
```

# Arguments:

  * `leaf_maps`: A vector of the dictionary mapping the leaf value's index to the FeynmanGraph/Graph of this leaf.               Each dict corresponds to a graph partition, such as (order, Gorder, Vorder).
  * `labelProd`: A LabelProduct used to label the leaves of graphs.

# Returns

  * A tuple of vectors containing information about the leaves of graphs, including their initial values, types, orders, input and output time indexes, and loop-momenta indexes.
