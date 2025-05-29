```
get_x(prob::PEtabODEProblem; linear_scale = false)::ComponentArray
```

Get the nominal parameter vector with parameters in the correct order expected by `prob` for parameter estimation/inference. Nominal values can optionally be specified when creating a `PEtabParameter`, or in the parameters table if the problem is provided in the PEtab standard format.

For ease of interaction (e.g., changing values), the parameter vector is returned as a `ComponentArray`.  For how to interact with a `ComponentArray`, see the documentation and the ComponentArrays.jl [documentation](https://github.com/jonniedie/ComponentArrays.jl).

See also [`PEtabParameter`](@ref).

## Keyword argument

  * `linear_scale`: Whether to return parameters on the linear scale. By default, parameters are returned on the scale they are estimated, which by default is `log10` as this often improves parameter estimation performance.
