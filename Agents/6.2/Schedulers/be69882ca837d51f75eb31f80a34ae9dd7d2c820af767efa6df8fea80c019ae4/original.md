```
Schedulers
```

Submodule containing all predefined schedulers of Agents.jl that can be used with [`StandardABM`](@ref).

Schedulers have a very simple interface. They are functions that take as an input the ABM and return an iterator over agent IDs: `f(model) -> iterator`. Notice that this iterator can be non-allocated specialized type or just a standard vector of IDs.

Schedulers have many purposes:

1. Can be given in [`StandardABM`](@ref) as a default scheduler. This functionality is only meaningful when the `agent_step!` has been configured. The function `schedule(model)` will return the scheduled IDs.
2. Can be used by a user when performing [manual scheduling](@ref advanced_scheduling) in case `agent_step!` has not been configured.
3. Can be used to globally filter agents by type/property/whatever. For example, one can use the [`ByProperty`](@ref) scheduler to simply obtain the list of all agent IDs that satisfy a particular property.

See also [Advanced scheduling](@ref advanced_scheduling) for making more advanced schedulers.
