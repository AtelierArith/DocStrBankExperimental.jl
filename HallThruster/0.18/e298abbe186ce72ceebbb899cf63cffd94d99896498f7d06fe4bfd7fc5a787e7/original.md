```julia
struct Geometry1D
```

Describes the geometry of a Hall thruster discharge channel.

# Fields

  * `channel_length::Float64`: The discharge channel length, in meters

  * `inner_radius::Float64`: The inner radius of the discharge channel, in meters

  * `outer_radius::Float64`: The outer radius of the discharge channel, in meters

  * `channel_area::Float64`: The discharge channel cross-sectional area, computed from `inner_radius` and `outer_radius`
