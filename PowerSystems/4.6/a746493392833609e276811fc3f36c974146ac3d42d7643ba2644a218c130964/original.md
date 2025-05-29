```
mutable struct LCLFilter <: Filter
    lf::Float64
    rf::Float64
    cf::Float64
    lg::Float64
    rg::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a LCL filter outside the converter, the [states](@ref S) are in the grid's reference frame

# Arguments

  * `lf::Float64`: Series inductance in p.u. of converter filter, validation range: `(0, nothing)`
  * `rf::Float64`: Series resistance in p.u. of converter filter, validation range: `(0, nothing)`
  * `cf::Float64`: Shunt capacitance in p.u. of converter filter, validation range: `(0, nothing)`
  * `lg::Float64`: Series inductance in p.u. of converter filter to the grid, validation range: `(0, nothing)`
  * `rg::Float64`: Series resistance in p.u. of converter filter to the grid, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the LCLFilter model are:

```
ir_cnv: Real current out of the converter,
ii_cnv: Imaginary current out of the converter,
vr_filter: Real voltage at the filter's capacitor,
vi_filter: Imaginary voltage at the filter's capacitor,
ir_filter: Real current out of the filter,
ii_filter: Imaginary current out of the filter
```

  * `n_states::Int`: (**Do not modify.**) LCLFilter has 6 states
