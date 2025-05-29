```
(fmu::FMU)(;dx::AbstractVector{<:Real},
             y::AbstractVector{<:Real},
             y_refs::AbstractVector{<:fmiValueReference},
             x::AbstractVector{<:Real}, 
             u::AbstractVector{<:Real},
             u_refs::AbstractVector{<:fmiValueReference},
             p::AbstractVector{<:Real},
             p_refs::AbstractVector{<:fmiValueReference},
             ec::AbstractVector{<:Real},
             t::Real)
```

Evaluates a `FMU` by setting the component state `x`, inputs `u` and/or time `t`. If no component is available, one is allocated. The result of the evaluation might be the system output `y` and/or state-derivative `dx`.  Not all options are available for any FMU type, e.g. setting state is not supported for CS-FMUs. Assertions will be generated for wrong use.

# Keywords

  * `dx`: An array to store the state-derivatives in. If not provided but necessary, a suitable array is allocated and returned. Not supported by CS-FMUs.
  * `y`: An array to store the system outputs in. If not provided but requested, a suitable array is allocated and returned.
  * `y_refs`: An array of value references to indicate which system outputs shall be returned.
  * `x`: An array containing the states to be set. Not supported by CS-FMUs.
  * `u`: An array containing the inputs to be set.
  * `u_refs`: An array of value references to indicate which system inputs want to be set.
  * `p`: An array of FMU parameters to be set.
  * `p_refs`: An array of parameter references to indicate which system parameter sensitivities need to be determined.
  * `ec`: An array of real valued implicit event conditions ("event indicators")
  * `t`: A scalar value holding the system time to be set.

# Returns (as Tuple)

  * `y::Union{AbstractVector{<:Real}, Nothing}`: The system output `y` (if requested, otherwise `nothing`).
  * `dx::Union{AbstractVector{<:Real}, Nothing}`: The system state-derivaitve (if ME-FMU, otherwise `nothing`).
  * `ec::Union{AbstractVector{<:Real}, Nothing}`: The system event indicators (if ME-FMU, otherwise `nothing`).
