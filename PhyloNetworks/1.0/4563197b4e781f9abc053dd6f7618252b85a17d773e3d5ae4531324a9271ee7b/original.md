```
rootatnode!(HybridNetwork, nodeNumber::Integer; index::Bool=false)
rootatnode!(HybridNetwork, Node)
rootatnode!(HybridNetwork, nodeName::AbstractString)
```

Root the network/tree object at the node with name 'nodeName' or number 'nodeNumber' (by default) or with index 'nodeNumber' if index=true. Attributes ischild1 and containroot are updated along the way. Use `plot(net, shownodenumber=true, showedgelength=false)` to visualize and identify a node of interest. (see package [PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl))

Return the network.

Warnings:

  * If the node is a leaf, the root will be placed along the edge adjacent to the leaf. This might add a new node.
  * If the desired root placement is incompatible with one or more hybrids, then

      * the original network is restored with its old root and edges' direction.
      * a RootMismatch error is thrown.

See also: [`rootonedge!`](@ref).
