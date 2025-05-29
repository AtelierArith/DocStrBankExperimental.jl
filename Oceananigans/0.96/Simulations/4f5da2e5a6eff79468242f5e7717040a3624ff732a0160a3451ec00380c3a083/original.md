```
TimeStepWizard([FT=Float64;]
               cfl = 0.2,
               diffusive_cfl = Inf,
               max_change = 1.1,
               min_change = 0.5,
               max_Δt = Inf,
               min_Δt = 0.0,
               cell_advection_timescale = cell_advection_timescale,
               cell_diffusion_timescale = infinite_diffusion_timescale)
```

Callback function that adjusts the simulation time step to meet specified target values for advective and diffusive Courant-Friedrichs-Lewy (CFL) numbers (`cfl` and `diffusive_cfl`), subject to the limits

```julia
max(min_Δt, min_change * last_Δt) ≤ new_Δt ≤ min(max_Δt, max_change * last_Δt)
```

where `new_Δt` is the new time step calculated by the `TimeStepWizard`.

For more information on the CFL number, see its [wikipedia entry](https://en.wikipedia.org/wiki/Courant%E2%80%93Friedrichs%E2%80%93Lewy_condition).

# Example

To use `TimeStepWizard`, insert it into a [`Callback`](@ref) and then add the `Callback` to a `Simulation`:

```julia
julia> simulation = Simulation(model, Δt=0.9, stop_iteration=100)

julia> wizard = TimeStepWizard(cfl=0.2)

julia> simulation.callbacks[:wizard] = Callback(wizard, IterationInterval(4))
```

Then when `run!(simulation)` is invoked, the time-step `simulation.Δt` will be updated every 4 iterations.

(Note that the name `:wizard` is unimportant.)
