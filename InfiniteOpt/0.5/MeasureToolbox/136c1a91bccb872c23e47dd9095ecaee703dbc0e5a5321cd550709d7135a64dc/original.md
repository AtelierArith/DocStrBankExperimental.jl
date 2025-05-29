```
set_multi_integral_defaults(; kwargs...)::Nothing
```

Set the default keyword argument settings for multi-dimesnional integrals. The keyword arguments of this function will be recorded in the default keyword argument dictionary. These will determine the default keyword argument values when calling [`integral`](@ref MeasureToolbox.integral(::JuMP.AbstractJuMPScalar,::AbstractArray{GeneralVariableRef},::Union{Real, AbstractArray{<:Real}}, ::Union{Real, AbstractArray{<:Real}})) with an array of infinite parameters.

**Example**

```julia-repl
julia> multi_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()

julia> set_multi_integral_defaults(num_supports = 5, new_kwarg = true)

julia> multi_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Automatic()
```
