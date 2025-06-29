```
struct Network <: AbstractNetwork
    graph::MetaGraphsNext.AbstractGraph
    substation_bus::String
    Sbase::Real
    Vbase::Real
    Zbase::Real
    v0::Union{Real, AbstractVecOrMat{<:Number}}
    Ntimesteps::Int
    bounds::VariableBounds
    var_names::AbstractVector{Symbol}
end
```

The `Network` model is used to store all the inputs required to create power flow and optimal power flow models. Underlying the Network model is a `MetaGraphsNext.MetaGraph` that stores the edge and node data in the network. 

We leverage the `AbstractNetwork` type to make an intuitive interface for the Network model. For example, `edges(network)` returns an iterator of edge tuples with bus name values; (but if we used `Graphs.edges(MetaGraph)` we would get an iterator of Graphs.SimpleGraphs.SimpleEdge with integer values).

A Network can be created directly, via a `Dict`, or a filepath. The minimum inputs must have a vector of [Conductor](@ref) specifications and a `Network` key containing at least the `substation_bus`. See [Input Formats](@ref) for more details.

`var_names` is empty be default. It is used in the results getters like `opf_results`.
