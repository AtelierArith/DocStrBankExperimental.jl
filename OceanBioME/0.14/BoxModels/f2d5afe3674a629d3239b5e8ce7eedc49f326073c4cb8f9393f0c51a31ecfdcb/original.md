```
BoxModel(; biogeochemistry,
           forcing = NamedTuple(),
           timestepper = :RungeKutta3,
           clock = Clock(; time = 0.0),
           prescribed_tracers::PT = NamedTuple())
```

Constructs a box model of a `biogeochemistry` model. Once this has been constructed you can set initial condiitons by `set!(model, X=1.0...)`.

# Keyword Arguments

  * `biogeochemistry`: (required) an OceanBioME biogeochemical model, most models must be passed a `grid` which can be set to a `BoxModelGrid` for box models
  * `forcing`: NamedTuple of additional forcing functions for the biogeochemical tracers to be integrated
  * `timestepper`: Timestepper to integrate model
  * `clock`: Oceananigans clock to keep track of time
  * `prescribed_tracers`: named tuple of tracer names and function (`f(t)`) prescribing tracer values
