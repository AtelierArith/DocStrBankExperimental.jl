```
display_rate_equation(
rate_equation::Function,
metab_names::Tuple{Symbol,Vararg{Symbol}},
param_names::Tuple{Symbol,Vararg{Symbol}};
nt_param_removal_code = nothing
```

)

Return the symbolic rate equation for the given `rate_equation` function.

# Arguments

  * `rate_equation::Function`: The rate equation function.
  * `metab_names::Tuple{Symbol,Vararg{Symbol}}`: The names of the metabolites.
  * `param_names::Tuple{Symbol,Vararg{Symbol}}`: The names of the parameters.
  * `nt_param_removal_code::NamedTuple`: The named tuple of the parameters to remove from the rate equation.
