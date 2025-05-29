```
ScaleNegativeTracers(; tracers, scalefactors = ones(length(tracers)), warn = false, invalid_fill_value = NaN)
```

Constructs a modifier to scale `tracers` so that none are negative. Use like:

```julia
modifier = ScaleNegativeTracers((:P, :Z, :N))
biogeochemistry = Biogeochemistry(...; modifier)
```

This method is better, though still imperfect, method to prevent numerical errors that lead to negative tracer values compared to [`ZeroNegativeTracers`](@ref). Please see [discussion in github](https://github.com/OceanBioME/OceanBioME.jl/discussions/48).

Future plans include implement a positivity-preserving timestepping scheme as the ideal alternative.

~~If `warn` is true then scaling will raise a warning.~~

`invalid_fill_value` specifies the value to set the total cell content to if the total is less than 0 (meaning that total tracer conservation can not be enforced). If the value is set to anything other than `NaN` this scheme no longer conserves mass. While this may be useful to prevent spurious numerics leading to crashing care should be taken that the mass doesn't deviate too much.

This scheme is similar to that used by [NEMO-PISCES](https://www.nemo-ocean.eu/), although they scale the tendency rather than the value, while other Earth system models simply set negative tracers to zero, for example [NCAR's MARBL](https://marbl-ecosys.github.io/versions/latest_release/index.html) and [NEMO-TOPAZ2](https://zenodo.org/records/2648099), which does not conserve mass. More complicated schemes exist, for example [ROMS-BECS](https://zenodo.org/records/3988618) uses an implicite-itterative approach where each component is updated in sequence to garantee mass conservation, possibly at the expense of numerical precision.
