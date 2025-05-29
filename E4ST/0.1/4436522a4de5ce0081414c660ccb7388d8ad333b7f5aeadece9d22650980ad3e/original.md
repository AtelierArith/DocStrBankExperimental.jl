```
setup_table!(config, data, ::Val{:nominal_load})
```

Set up the load table.

Also calls the following:

  * [`shape_nominal_load!(config, data)`](@ref) - scales hourly load power by an hourly load profile by arbitrary region
  * [`match_nominal_load!(config, data)`](@ref) - matches annual load energy by arbitrary region
  * [`add_nominal_load!(config, data)`](@ref) - adds hourly load power by arbitrary region
