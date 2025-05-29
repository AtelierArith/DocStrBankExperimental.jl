```julia
struct TimeStepOptions
```

struct containing options controlling the size and calculation of time steps.

See also: [`SimulationConfig`](@ref)

# Examples

```jldoctest
julia> using UltraDark

julia> TimeStepOptions()
TimeStepOptions(10, 1.0)
```

# Fields

  * `update_period::Int64`: controls how many steps are taken before the timestep is updated
  * `multiplier::Float64`: multiplies the calculated maximum time step by a constant
