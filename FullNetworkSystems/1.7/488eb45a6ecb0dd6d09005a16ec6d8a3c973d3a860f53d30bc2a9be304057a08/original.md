```julia
struct Generator
```

Type for static generator attribute (i.e. things that describe a generator that are not time series data).  Parameters given in `pu` assume a base power of 100MW.

Fields:

  * `unit_code::Int64`: Generator id/unit code
  * `zone::Int64`: Number of the zone the generator is located in
  * `startup_cost::Float64`: Cost of turning on the generator ($)
  * `shutdown_cost::Float64`: Cost of turning off the generator ($)
  * `no_load_cost::Float64`: Cost of the generator being on but not producing any MW ($ /hour)
  * `min_uptime::Float64`: Minimum time the generator has to be committed for (hours)
  * `min_downtime::Float64`: Minimum time the generator has to be off for (hours)
  * `ramp_up::Float64`: Rate at which the generator can increase generation (pu/minute)
  * `ramp_down::Float64`: Rate at which the generator can decrease generation (pu/minute)
  * `technology::Symbol`: Symbol describing the technology of the generator
