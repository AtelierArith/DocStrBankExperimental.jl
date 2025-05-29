```
add_time_vector_variables!(
    m::JuMP.AbstractModel, 
    net::Network{SinglePhase}, 
    var_symbol::Symbol, 
    indices::AbstractVector{T} 
) where {T}
```

Add variables to the `m.obj_dict` indexed on:

1. `var_symbol` like `:v`
2. `indices`, typically a `Vector{String}` for bus indices or a `Vector{Tuple{String, String}}` for edge indices (like `("bus1", "bus2")`)
3. timesteps in `1:net.Ntimesteps`

For example, accessing the edge variable `:sij` one edge `("bus1", "bus2")` voltage variable at time step `5` looks like:

```julia
m[:sij][("bus1", "bus2")][5]
```
