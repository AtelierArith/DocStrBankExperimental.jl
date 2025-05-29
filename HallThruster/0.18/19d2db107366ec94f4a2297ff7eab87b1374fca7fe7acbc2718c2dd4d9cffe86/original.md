```julia
mutable struct SimParams{C<:HallThruster.CurrentController}
```

  * `grid::HallThruster.GridSpec`: A grid specifier, either `HallThruster.EvenGrid(n)` or `HallThruster.UnevenGrid(n)`, where n is the desired number of cells. See [Grid generation](@ref) for more information.

  * `dt::Float64`: The simulation base timestep in seconds. See [Timestepping](@ref) for more info.

  * `duration::Float64`: The simulation duration in seconds.

  * `num_save::Int64`: How many simulation frames to save in the `Solution` struct. **Default:** 1000

  * `verbose::Bool`: Whether information such as the simulation run-time is printed to console. **Default:** `true`

  * `print_errors::Bool`: Whether errors are printed to console in addition to being captured in the `Solution` struct. **Default:** `true`

  * `adaptive::Bool`: Whether to use adaptive timestepping. See [Timestepping](@ref) for more info. **Default:** `true`

  * `CFL::Float64`: The CFL number used in adaptive timestepping. Maximum is 0.799. **Default:** 0.799

  * `min_dt::Float64`: The minimum allowable timestep in adaptive timestepping, in seconds. **Default:** 1e-10

  * `max_dt::Float64`: The maximum allowable timestep in adaptive timestepping, in seconds. **Default:** 1e-7

  * `max_small_steps::Int64`: The maximum number of minimally-sized timesteps permitted in adaptive timestepping. **Default:** 100

  * `current_control::HallThruster.CurrentController`: Discharge current controller. **Default:** `HallThruster.NoController()`
