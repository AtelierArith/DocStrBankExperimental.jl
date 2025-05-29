```
rootonedge!(HybridNetwork, edgeNumber::Integer; index::Bool=false)
rootonedge!(HybridNetwork, Edge)
```

Root the network/tree along an edge with number `edgeNumber` (by default) or with index `edgeNumber` if `index=true`. Attributes `ischild1` and `containroot` are updated along the way.

This adds a new node and a new edge to the network. Use `plot(net, showedgenumber=true, showedgelength=false)` to visualize and identify an edge of interest. (see package [PhyloPlots](https://github.com/juliaphylo/PhyloPlots.jl))

See also: [`rootatnode!`](@ref).
