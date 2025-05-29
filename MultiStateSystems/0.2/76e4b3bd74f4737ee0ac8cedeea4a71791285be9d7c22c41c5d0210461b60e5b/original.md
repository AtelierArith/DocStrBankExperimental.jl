```
add_users!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

Adds multiple users to the network `ntw` and fills their corresponding `PropDict` with the named arguments `kwargs`. Either an uniform arguments is given which holds for all components or an array is given whith specific argument for each component.

# Example

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_sources!(ntwᵖʷʳ, node = [1,5,8],
                            ind  = [:EENS])
```
