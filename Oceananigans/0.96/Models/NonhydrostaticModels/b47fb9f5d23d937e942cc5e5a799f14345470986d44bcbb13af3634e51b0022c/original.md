```
NonhydrostaticModel(;           grid,
                                clock = Clock{eltype(grid)}(time = 0),
                            advection = Centered(),
                             buoyancy = nothing,
                             coriolis = nothing,
                         stokes_drift = nothing,
                  forcing::NamedTuple = NamedTuple(),
                              closure = nothing,
      boundary_conditions::NamedTuple = NamedTuple(),
                              tracers = (),
                          timestepper = :RungeKutta3,
        background_fields::NamedTuple = NamedTuple(),
        particles::ParticlesOrNothing = nothing,
biogeochemistry::AbstractBGCOrNothing = nothing,
                           velocities = nothing,
              nonhydrostatic_pressure = CenterField(grid),
         hydrostatic_pressure_anomaly = DefaultHydrostaticPressureAnomaly(),
                   diffusivity_fields = nothing,
                      pressure_solver = nothing,
                     auxiliary_fields = NamedTuple())
```

Construct a model for a non-hydrostatic, incompressible fluid on `grid`, using the Boussinesq approximation when `buoyancy != nothing`. By default, all Bounded directions are rigid and impenetrable.

# Keyword arguments

  * `grid`: (required) The resolution and discrete geometry on which the `model` is solved. The         architecture (CPU/GPU) that the model is solved on is inferred from the architecture         of the `grid`. Note that the grid needs to be regularly spaced in the horizontal         dimensions, $x$ and $y$.
  * `advection`: The scheme that advects velocities and tracers. See `Oceananigans.Advection`.
  * `buoyancy`: The buoyancy model. See `Oceananigans.BuoyancyFormulations`.
  * `coriolis`: Parameters for the background rotation rate of the model.
  * `stokes_drift`: Parameters for Stokes drift fields associated with surface waves. Default: `nothing`.
  * `forcing`: `NamedTuple` of user-defined forcing functions that contribute to solution tendencies.
  * `closure`: The turbulence closure for `model`. See `Oceananigans.TurbulenceClosures`.
  * `boundary_conditions`: `NamedTuple` containing field boundary conditions.
  * `tracers`: A tuple of symbols defining the names of the modeled tracers, or a `NamedTuple` of            preallocated `CenterField`s.
  * `timestepper`: A symbol that specifies the time-stepping method. Either `:QuasiAdamsBashforth2` or                `:RungeKutta3` (default).
  * `background_fields`: `NamedTuple` with background fields (e.g., background flow). Default: `nothing`.
  * `particles`: Lagrangian particles to be advected with the flow. Default: `nothing`.
  * `biogeochemistry`: Biogeochemical model for `tracers`.
  * `velocities`: The model velocities. Default: `nothing`.
  * `nonhydrostatic_pressure`: The nonhydrostatic pressure field. Default: `CenterField(grid)`.
  * `hydrostatic_pressure_anomaly`: An optional field that stores the part of the nonhydrostatic pressure                                 in hydrostatic balance with the buoyancy field. If `CenterField(grid)` (default), the anomaly is precomputed by                                 vertically integrating the buoyancy field. In this case, the `nonhydrostatic_pressure` represents                                 only the part of pressure that deviates from the hydrostatic anomaly. If `nothing`, the anomaly                                 is not computed.
  * `diffusivity_fields`: Diffusivity fields. Default: `nothing`.
  * `pressure_solver`: Pressure solver to be used in the model. If `nothing` (default), the model constructor chooses the default based on the `grid` provide.
  * `auxiliary_fields`: `NamedTuple` of auxiliary fields. Default: `nothing`
