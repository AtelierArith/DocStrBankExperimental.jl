```
is_depleted(point_types::PointTypes)::Bool
```

Returns `true` if all [`PointType`](@ref) values of the [`PointTypes`](@ref) of a [`Simulation`](@ref) are marked as depleted and `false` if any point in the [`PointTypes`](@ref) is marked as undepleted.

It can be used to determine whether the [`SolidStateDetector`](@ref) is depleted at the provided bias voltage.

## Arguments

  * `point_types::PointTypes`: [`PointTypes`](@ref) of a [`Simulation`](@ref).

## Examples

```julia
is_depleted(sim.point_types)
```
