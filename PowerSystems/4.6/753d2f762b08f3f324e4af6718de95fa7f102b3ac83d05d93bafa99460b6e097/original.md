```
mutable struct Arc <: Topology
    from::Bus
    to::Bus
    internal::InfrastructureSystemsInternal
end
```

A topological directed edge connecting two buses.

Arcs are used to define the `from` and `to` buses when defining a line or transformer

# Arguments

  * `from::Bus`: The initial bus
  * `to::Bus`: The terminal bus
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
