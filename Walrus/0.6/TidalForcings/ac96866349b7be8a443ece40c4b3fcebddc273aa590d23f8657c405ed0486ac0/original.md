```
TidalForcing(; x_amplitude,
               y_amplitude,
               period = 12.3782216453hours,
               nodal_time = 0.,
               x_lag = 0.,
               y_lag = 0.,
               coriolis = nothing)
```

A convenience constructor for `Tide` which returns the forcings pre wrapped.

# Keyword Arguments

  * `x_amplitude`: the tidal amplitude in the x direction
  * `y_amplitude`: the tidal amplitude in the x direction
  * `period`: the tidal period (defaults to that of an M2 tide)
  * `nodal_time`: the time at which peak flow occurs
  * `x_lag`: the phase lag for the tidal component in the x direction
  * `y_lag`: the phase lag for the tidal component in the y direction
  * `coriolis`: a model for the coriolis parameter

# Example

```jldoctest
julia> using Walrus: TidalForcing

julia> tidal_forcing = TidalForcing(x_amplitude = 0.1, y_amplitude = 0.)
(u = DiscreteForcing{Val{:x}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:x}(), v = DiscreteForcing{Val{:y}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:y}())
```
