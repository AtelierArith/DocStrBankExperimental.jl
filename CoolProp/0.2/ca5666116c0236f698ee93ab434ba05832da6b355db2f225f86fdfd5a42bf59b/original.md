```
AbstractState_first_saturation_deriv(handle::Clong, of::Clong, wrt::Clong)
```

Calculate a saturation derivative from the AbstractState using integer values for the desired parameters.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `of`: The parameter of which the derivative is being taken
  * `wrt`: The derivative with with respect to this parameter

# Example

```julia
julia> as = AbstractState_factory("HEOS", "Water");
julia> AbstractState_update(as, "PQ_INPUTS", 15e5, 0);
julia> AbstractState_first_saturation_deriv(as, get_param_index("Hmolar"), get_param_index("P"))
0.0025636362140578207
```

# Ref

double CoolProp::AbstractState*first*saturation*deriv(const long handle, const long Of, const long Wrt, long* errcode, char* message*buffer, const long buffer_length);
