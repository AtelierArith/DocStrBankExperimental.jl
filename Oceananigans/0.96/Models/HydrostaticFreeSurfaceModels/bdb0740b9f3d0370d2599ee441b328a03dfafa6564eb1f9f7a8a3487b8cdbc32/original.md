```
HydrostaticFreeSurfaceModel(; grid,
                            clock = Clock{Float64}(time = 0),
                            momentum_advection = VectorInvariant(),
                            tracer_advection = Centered(),
                            buoyancy = SeawaterBuoyancy(eltype(grid)),
                            coriolis = nothing,
                            free_surface = default_free_surface(grid, gravitational_acceleration=g_Earth),
                            forcing::NamedTuple = NamedTuple(),
                            closure = nothing,
                            timestepper = :QuasiAdamsBashforth2,
                            boundary_conditions::NamedTuple = NamedTuple(),
                            tracers = (:T, :S),
                            particles::ParticlesOrNothing = nothing,
                            biogeochemistry::AbstractBGCOrNothing = nothing,
                            velocities = nothing,
                            pressure = nothing,
                            diffusivity_fields = nothing,
                            auxiliary_fields = NamedTuple(),
                            vertical_coordinate = default_vertical_coordinate(grid))
```

Construct a hydrostatic model with a free surface on `grid`.

# Keyword arguments

  * `grid`: (required) The resolution and discrete geometry on which `model` is solved. The         architecture (CPU/GPU) that the model is solved is inferred from the architecture         of the `grid`.
  * `momentum_advection`: The scheme that advects velocities. See `Oceananigans.Advection`.
  * `tracer_advection`: The scheme that advects tracers. See `Oceananigans.Advection`.
  * `buoyancy`: The buoyancy model. See `Oceananigans.BuoyancyFormulations`.
  * `coriolis`: Parameters for the background rotation rate of the model.
  * `free_surface`: The free surface model. The default free-surface solver depends on the                 geometry of the `grid`. If the `grid` is a `RectilinearGrid` that is                 regularly spaced in the horizontal the default is an `ImplicitFreeSurface`                 solver with `solver_method = :FFTBasedPoissonSolver`. In all other cases,                 the default is a `SplitExplicitFreeSurface`.
  * `tracers`: A tuple of symbols defining the names of the modeled tracers, or a `NamedTuple` of            preallocated `CenterField`s.
  * `forcing`: `NamedTuple` of user-defined forcing functions that contribute to solution tendencies.
  * `closure`: The turbulence closure for `model`. See `Oceananigans.TurbulenceClosures`.
  * `timestepper`: A symbol that specifies the time-stepping method.                Either `:QuasiAdamsBashforth2` (default) or `:SplitRungeKutta3`.
  * `boundary_conditions`: `NamedTuple` containing field boundary conditions.
  * `particles`: Lagrangian particles to be advected with the flow. Default: `nothing`.
  * `biogeochemistry`: Biogeochemical model for `tracers`.
  * `velocities`: The model velocities. Default: `nothing`.
  * `pressure`: Hydrostatic pressure field. Default: `nothing`.
  * `diffusivity_fields`: Diffusivity fields. Default: `nothing`.
  * `auxiliary_fields`: `NamedTuple` of auxiliary fields. Default: `nothing`.
  * `vertical_coordinate`: Algorithm for grid evolution: ZStar() or ZCoordinate().                        Default: ZStar() for grids with MutableVerticalDiscretization;                        ZCoordinate() otherwise.
