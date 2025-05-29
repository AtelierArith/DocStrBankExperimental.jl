```
mutable struct LCFilter <: Filter
    lf::Float64
    rf::Float64
    cf::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a LCL filter outside the converter

# Arguments

  * `lf::Float64`: filter inductance, validation range: `(0, nothing)`
  * `rf::Float64`: filter resistance, validation range: `(0, nothing)`
  * `cf::Float64`: filter capacitance, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the LCFilter model are:

```
ir_filter: Real current out of the filter,
ii_filter: Imaginary current out of the filter
```

  * `n_states::Int`: (**Do not modify.**) LCFilter has two states
