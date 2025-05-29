```
get_parameter_information_string(key::AbstractString, outtype::AbstractString)
get_parameter_information_string(key::AbstractString)
```

Get information for a parameter.

# Arguments

  * `key`: A string represents parameter name, to see full list check "Table of string inputs to PropsSI function": http://www.coolprop.org/coolprop/HighLevelAPI.html#parameter-table, or simply type `get_global_param_string("parameter_list")`
  * `outtype="long"`: Output type, could be one of the `["IO", "short", "long", "units"]`, with a default value of "long"

# Example

```julia
julia> get_parameter_information_string("HMOLAR")
"Molar specific enthalpy"
julia> get_parameter_information_string("HMOLAR", "units")
"J/mol"
```

# Note

A tabular output for this function is available with `?CoolProp_parameters`
