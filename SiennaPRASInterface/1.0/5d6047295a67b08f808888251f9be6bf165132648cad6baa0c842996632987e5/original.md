```
GeneratorPRAS(; max_active_power, lump_renewable_generation) <: AbstractRAFormulation
```

# Arguments

  * `max_active_power::String`: Name of time series to use for max active power
  * `lump_renewable_generation::Bool`: Whether to lump renewable generation to regions

GeneratorPRAS produces generator entries in PRAS.
