```
LoadLimits{T<:Real} <: AbstractLoadLimits{T}
```

Type for the incorporation of limits on the capacity utilization of the node through constraining the variable [`:cap_use`](@extref EnergyModelsBase man-opt_var-cap).

# Fields

  * **`min`** is the minimum load as fraction of the installed capacity.
  * **`max`** is the maximum load as fraction of the installed capacity.
