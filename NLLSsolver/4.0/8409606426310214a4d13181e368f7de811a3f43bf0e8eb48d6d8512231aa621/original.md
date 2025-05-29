```
NLLSsolver.getvars(mycost, vars)
```

Return the variables that `mycost` depends on. The return value must be a tuple of variables.

For good performance, is important that the output variables have concrete types, e.g. not  `Any`.

# Example

For a problem `MyCost <: AbstractCost` that depends on the first and third variables,

```julia
    NLLSsolver.getvars(::MyCost, vars) = (vars[1], vars[3])
```

!!! tip
    If `vars` is heterogeneous in type, add type-annotations to the specific variables, e.g.


`(vars[1]::Matrix{T}, vars[3]::Vector{T})` for a `MyCost{T}`.

!!! note
    Required user-specialized API function.

