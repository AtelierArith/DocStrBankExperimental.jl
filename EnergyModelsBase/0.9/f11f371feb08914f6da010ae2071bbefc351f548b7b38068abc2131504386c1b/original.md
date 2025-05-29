```
variables_node(m, 𝒩ˢⁱⁿᵏ::Vector{<:Sink}, 𝒯, modeltype::EnergyModel)
```

When the node vector is a `Vector{<:Sink}`, both surplus (`:sink_surplus`) and deficit (`:sink_deficit`) variables are created to quantify when there is too much or too little energy for satisfying the demand.
