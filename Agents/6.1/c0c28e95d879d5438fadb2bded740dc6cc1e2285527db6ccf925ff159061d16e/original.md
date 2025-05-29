```
ContinuousSpace(extent::NTuple{D, <:Real}; kwargs...)
```

Create a `D`-dimensional `ContinuousSpace` in range 0 to (but not including) `extent`. Your agent positions (field `pos`) must be of type `SVector{D, <:Real}`, and it is strongly recommend that agents also have a field `vel::SVector{D, <:Real}` to use in conjunction with [`move_agent!`](@ref). Use [`ContinuousAgent`](@ref) for convenience.

`ContinuousSpace` is a representation of agent dynamics on a continuous medium where agent position, orientation, and speed, are true floats. In addition, support is provided for representing spatial properties in a model that contains a `ContinuousSpace`. Spatial properties (which typically are contained in the model properties) can either be functions of the position vector, `f(pos) = value`, or `AbstractArrays`, representing discretizations of spatial data that may not be available in analytic form. In the latter case, the position is automatically mapped into the discretization represented by the array. Use [`get_spatial_property`](@ref) to access spatial properties in conjunction with `ContinuousSpace`.

See also [Continuous space exclusives](@ref) on the online docs for more functionality. An example using continuous space is the [Flocking model](@ref).

## Distance specification

Distances specified by `r` in functions like [`nearby_ids`](@ref) are always based on the Euclidean distance between two points in `ContinuousSpace`.

In `ContinuousSpace` `nearby_*` searches are accelerated using a grid system; see discussion around the keyword `spacing` below. By default, `nearby_*` has the keyword  `search` set to `:approximate`, which means that it doesn't do an exact search, but  can be a possible overestimation, including agent IDs whose distance slightly exceeds  `r` with "slightly" being as much as `spacing`. If you want exact searches set the keyword  `search` to `:exact` in `nearby_*`.

## Keywords

  * `periodic = true`: Whether the space is periodic or not. If set to `false` an error will occur if an agent's position exceeds the boundary.
  * `spacing::Real = minimum(extent)/20`: Configures an internal compartment spacing that is used to accelerate nearest neighbor searches like [`nearby_ids`](@ref). The compartments are actually a full instance of `GridSpace` in which agents move. All dimensions in `extent` must be completely divisible by `spacing`. There is no best choice for the value of `spacing` and if you need optimal performance it's advised to set up a benchmark over a range of choices. The finer the spacing, the faster and more accurate the inexact version of `nearby_ids` becomes. However, a finer spacing also means slower `move_agent!`, as agents change compartments more often.
  * `update_vel!`: A **function**, `update_vel!(agent, model)` that updates the agent's velocity **before** the agent has been moved, see [`move_agent!`](@ref). You can of course change the agents' velocities during the agent interaction, the `update_vel!` functionality targets spatial force fields acting on the agents individually (e.g. some magnetic field). If you use `update_vel!`, the agent type must have a field `vel::SVector{D, <:Real}`.
