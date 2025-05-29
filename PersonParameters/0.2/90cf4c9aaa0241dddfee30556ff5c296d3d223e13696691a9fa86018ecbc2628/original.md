```julia
struct PersonParameter{U<:Real}
```

A container holding a single estimated person parameter.

## Fields

  * `value`: the estimated ability value
  * `se`: the estimated standard error

## Methods

  * [`value`](@ref): Extract the person parameter estimate
  * [`se`](@ref): Extract the standard error of estimation
