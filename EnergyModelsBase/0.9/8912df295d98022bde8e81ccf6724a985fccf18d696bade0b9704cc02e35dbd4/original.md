```
struct GenAvailability <: Availability
```

A reference `Availability` node. The reference `Availability` node solves the energy balance for all connected flows.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`inputs::Vector{<:Resource}`** are the input [`Resource`](@ref)s.
  * **`output::Vector{<:Resource}`** are the output [`Resource`](@ref)s.

A constructor is provided so that only a single array can be provided with the fields:

  * **`id`** is the name/identifier of the node.
  * **`𝒫::Vector{<:Resource}`** are the `[`Resource`](@ref)s.
