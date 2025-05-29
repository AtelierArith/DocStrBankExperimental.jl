```
add_components!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds multiple components to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`. Either an uniform arguments is given which holds for all components or an array is given whith specific argument for each component.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_components!(ntwᵖʷʳ, edge = [(1,2),(1,2),(2,3)],
                               name = ["cable 1","cable 2","cable 3"],
                               std  = [STD(power = [0u"MW",1500u"MW"],
                                           prob  = [0.2,0.8]),
                                       STD(power = [0u"MW",2000u"MW"],
                                           prob  = [0.4,0.6]),
                                       STD(power = [0u"MW",1800u"MW",4000u"MW"],
                                           prob = [0.1,0.2,0.7])])
```
