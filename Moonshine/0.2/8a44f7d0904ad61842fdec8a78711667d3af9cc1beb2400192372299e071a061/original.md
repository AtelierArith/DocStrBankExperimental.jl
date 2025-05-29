```julia
abstract type AbstractGenealogy <: Graphs.SimpleGraphs.AbstractSimpleGraph{Int32}
```

Abstract type for genealogies.

Implements [the Graphs.jl interface](https://juliagraphs.org/Graphs.jl/stable/ecosystem/interface/) so that subtypes implementing the AbstractGenealogy interface can additionally be treated as regular graphs.

[Tree](@ref) & [Arg](@ref) are subtypes that implement the AbstractGenealogy interface.
