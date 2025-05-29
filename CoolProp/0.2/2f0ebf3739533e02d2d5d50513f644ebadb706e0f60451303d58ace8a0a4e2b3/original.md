```
AbstractState_set_fluid_parameter_double(handle::Clong, i::Integer, parameter::AbstractString, value::Real)
```

Set some fluid parameter (ie volume translation for cubic). Currently applied to the whole fluid not to components.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `i`: indice of the fluid the parameter should be applied to (for mixtures)
  * `parameter`: string wit the name of the parameter, e.g. "c", "cm", "c_m" for volume translation parameter.
  * `value`: the value of the parameter
