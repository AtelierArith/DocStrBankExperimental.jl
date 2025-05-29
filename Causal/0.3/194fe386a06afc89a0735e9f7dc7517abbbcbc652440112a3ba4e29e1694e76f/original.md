```julia
struct Model{GR, ND, BR, TM, CB}
```

A `Model` consists of nodes and branches. Nodes are connected to each other through the branches. A `Model` instance is ready for simulation.

See also [`Node`](@ref), [`Branch`](@ref)

# Fields

!!! warning `Model`s are units that can be simulated. As the data flows through the branches i.e. input output busses of the     components, its is important that the components must be connected to each other. See also: [`simulate!`](@ref)
