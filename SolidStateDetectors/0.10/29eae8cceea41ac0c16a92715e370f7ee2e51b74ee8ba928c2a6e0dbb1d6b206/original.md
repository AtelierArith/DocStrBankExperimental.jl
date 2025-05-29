```
get_active_volume(point_types::PointTypes{T}) where {T}
```

Returns an approximation of the active volume of the detector by summing up the cell volumes of all cells marked as depleted.

## Arguments

  * `point_types::PointTypes{T}`: Point types of a [`Simulation`](@ref).

## Examples

```
get_active_volume(sim.point_types)
```

!!! note
    Only `φ`-symmetries are taken into account.

