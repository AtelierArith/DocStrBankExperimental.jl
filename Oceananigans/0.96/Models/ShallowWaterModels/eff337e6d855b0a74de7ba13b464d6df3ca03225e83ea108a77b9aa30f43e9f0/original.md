```
ShallowWaterModel(; grid,
                    gravitational_acceleration,
                          clock = Clock{eltype(grid)}(time = 0),
             momentum_advection = UpwindBiased(order=5),
               tracer_advection = WENO(),
                 mass_advection = WENO(),
                       coriolis = nothing,
            forcing::NamedTuple = NamedTuple(),
                        closure = nothing,
                     bathymetry = nothing,
                        tracers = (),
             diffusivity_fields = nothing,
boundary_conditions::NamedTuple = NamedTuple(),
            timestepper::Symbol = :RungeKutta3,
                    formulation = ConservativeFormulation())
```

Construct a shallow water model on `grid` with `gravitational_acceleration` constant.

# Keyword arguments

  * `grid`: (required) The resolution and discrete geometry on which `model` is solved. The         architecture (CPU/GPU) that the model is solve is inferred from the architecture         of the grid.
  * `gravitational_acceleration`: (required) The gravitational acceleration constant.
  * `clock`: The `clock` for the model.
  * `momentum_advection`: The scheme that advects velocities. See `Oceananigans.Advection`. Default: `UpwindBiased(order=5)`.
  * `tracer_advection`: The scheme that advects tracers. See `Oceananigans.Advection`. Default: `WENO()`.
  * `mass_advection`: The scheme that advects the mass equation. See `Oceananigans.Advection`. Default: `WENO()`.
  * `coriolis`: Parameters for the background rotation rate of the model.
  * `forcing`: `NamedTuple` of user-defined forcing functions that contribute to solution tendencies.
  * `closure`: The turbulence closure for `model`. See `Oceananigans.TurbulenceClosures`.
  * `bathymetry`: The bottom bathymetry.
  * `tracers`: A tuple of symbols defining the names of the modeled tracers, or a `NamedTuple` of            preallocated `CenterField`s.
  * `diffusivity_fields`: Stores diffusivity fields when the closures require a diffusivity to be                       calculated at each timestep.
  * `boundary_conditions`: `NamedTuple` containing field boundary conditions.
  * `timestepper`: A symbol that specifies the time-stepping method. Either `:QuasiAdamsBashforth2` or                `:RungeKutta3` (default).
  * `formulation`: Whether the dynamics are expressed in conservative form (`ConservativeFormulation()`;                default) or in non-conservative form with a vector-invariant formulation for the                non-linear terms (`VectorInvariantFormulation()`).

!!! warning "Formulation-grid compatibility requirements"
    The `ConservativeFormulation()` requires `RectilinearGrid`. Use `VectorInvariantFormulation()` with `LatitudeLongitudeGrid`.

