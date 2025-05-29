```
set_uni_integral_defaults(; kwargs...)::Nothing
```

Set the default keyword argument settings for one-dimensional integrals. The keyword arguments of this function will be recorded in the default keyword argument dictionary. These will determine the default keyword argument values when calling [`integral`](@ref MeasureToolbox.integral(::JuMP.AbstractJuMPScalar,::InfiniteOpt.GeneralVariableRef,::Real, ::Real)) with a single infinite parameter.

**Example**

```julia-repl
julia> uni_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()


julia> set_uni_integral_defaults(num_supports = 5, eval_method = Quadrature(),
                                 new_kwarg = true)

julia> uni_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Quadrature()
```
