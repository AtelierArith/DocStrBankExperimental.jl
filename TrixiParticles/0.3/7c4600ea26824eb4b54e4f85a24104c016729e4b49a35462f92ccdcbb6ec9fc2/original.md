```
Semidiscretization(systems...; neighborhood_search=GridNeighborhoodSearch{NDIMS}())
```

The semidiscretization couples the passed systems to one simulation.

# Arguments

  * `systems`: Systems to be coupled in this semidiscretization

# Keywords

  * `neighborhood_search`:    The neighborhood search to be used in the simulation.                           By default, the [`GridNeighborhoodSearch`](@ref) is used.                           Use `nothing` to loop over all particles (no neighborhood search).                           To use other neighborhood search implementations, pass a template                           of a neighborhood search. See [`copy_neighborhood_search`](@ref)                           and the examples below for more details.                           To use a periodic domain, pass a [`PeriodicBox`](@ref) to the                           neighborhood search.
  * `threaded_nhs_update=true`:   Can be used to deactivate thread parallelization in the neighborhood search update.                               This can be one of the largest sources of variations between simulations                               with different thread numbers due to particle ordering changes.

# Examples

```jldoctest; output = false, setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), sol=nothing); ref_system = fluid_system)
semi = Semidiscretization(fluid_system, boundary_system)

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=GridNeighborhoodSearch{2}(update_strategy=SerialUpdate()))

periodic_box = PeriodicBox(min_corner = [0.0, 0.0], max_corner = [1.0, 1.0])
semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=GridNeighborhoodSearch{2}(; periodic_box))

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=PrecomputedNeighborhoodSearch{2}())

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=nothing)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ Semidiscretization                                                                               │
│ ══════════════════                                                                               │
│ #spatial dimensions: ………………………… 2                                                                │
│ #systems: ……………………………………………………… 2                                                                │
│ neighborhood search: ………………………… TrivialNeighborhoodSearch                                        │
│ total #particles: ………………………………… 636                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
