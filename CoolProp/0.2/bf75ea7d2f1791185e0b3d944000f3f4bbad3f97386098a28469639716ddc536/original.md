```
AbstractState_first_partial_deriv(handle::Clong, of::Clong, wrt::Clong, constant::Clong)
```

Calculate the first partial derivative in homogeneous phases from the AbstractState using integer values for the desired parameters.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `of`: The parameter of which the derivative is being taken
  * `Wrt`: The derivative with with respect to this parameter
  * `Constant`: The parameter that is not affected by the derivative

# Example

```julia
julia> as = AbstractState_factory("HEOS", "Water");
julia> AbstractState_update(as, "PQ_INPUTS", 15e5, 0);
julia> AbstractState_first_partial_deriv(as, get_param_index("Hmolar"), get_param_index("P"), get_param_index("S"))
2.07872526058326e-5
julia> AbstractState_first_partial_deriv(as, get_param_index("Hmolar"), get_param_index("P"), get_param_index("D"))
5.900781297636475e-5
```

# Ref

double CoolProp::AbstractState*first*partial*deriv(const long handle, const long Of, const long Wrt, const long Constant, long* errcode, char* message*buffer, const long buffer_length);
