```
connect(pnet::Workflow_PetriNet, place_port::Vector{Tuple{Place, Symbol}})
connect(pnet::Workflow_PetriNet, port_place::Vector{Tuple{Symbol, Place}})
```

Given a Petri net, connects the given places to a port of name port*name and type port*type. 

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref).
