DICE2023()

Parameters constructor with defaults aligned to DICE2023. 

Create a parameters struct with the defaults of the DICE2023 model. Different parameters, either the "raw" ones or the "computed ones", can be specified using keywork arguments.

See [`DICEParameters`](@ref) for a complete list of available parameters.

# Example

```julia
alt_dam_scen = DICE2023(a2base = [0.01]) # single value array parameter for the "world region"
```

# Note

  * Even if DICE2023 treats the World as a single region, the model works with a "regional" dimension, so all parameters (except those related to the carbon cycle) should be entered as a single-value array for static data or a (ntime_periods by nregions) matrix for (computed) dynamic parameters.
