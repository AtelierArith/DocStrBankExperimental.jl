```
add_sources!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds multiple sources to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`. Either an uniform arguments is given which holds for all components or an array is given whith specific argument for each component.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> stdᵍᵉⁿ = solvedSTD(prob = [0.1,0.2,0.7],
                          flow = [0.0u"MW",0.5u"MW",2.0u"MW"])
julia> add_sources!(ntwᵖʷʳ, node = 1:5,
                            std  = stdᵍᵉⁿ,
                            dep  = true)
```
