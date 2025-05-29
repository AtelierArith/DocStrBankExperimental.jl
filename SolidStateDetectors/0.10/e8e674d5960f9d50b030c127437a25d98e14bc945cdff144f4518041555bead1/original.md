```
Grid(sim::Simulation{T, Cartesian}; kwargs...)
Grid(sim::Simulation{T, Cylindrical}; kwargs...)
```

Initializes a [`Grid`](@ref) based on the objects defined in a [`Simulation`](@ref).

The important points of all objects are sampled and added to the ticks of the grid. The grid initialization can be tuned using a set of keyword arguments listed below.

## Arguments

  * `sim::Simulation{T, S}`: [`Simulation`](@ref) for which the grid will be defined.

## Keywords

  * `max_tick_distance = missing`: Maximum distance between neighbouring ticks of the grid.   Additional grid ticks will be added if two neighbouring ticks are too far apart.   `max_tick_distance` can either be a `Quantity`, e.g. `1u"mm"`, or a Tuple of `Quantity`,    e.g. `(1u"mm", 15u"°", 3u"mm")`,   to set it for each axis of the `Grid` separately. Note that a `CartesianGrid3D` requires a    `Tuple{LengthQuantity, LengthQuantity, LengthQuantity}` while a `CylindricalGrid` requires a   `Tuple{LengthQuantity, AngleQuantity, LengthQuantity}`.   If `max_tick_distance` is `missing`, one fourth of the axis length is used.
  * `max_distance_ratio::Real = 5`: If the ratio between a tick and its left and right neighbour  is greater than `max_distance_ratio`, additional ticks are added between the ticks that are  further apart. This prevents the ticks from being too unevenly spaced.
  * `add_ticks_between_important_ticks::Bool = true`: If set to `true`, additional points   will be added in between the important points obtained from sampling the objects of the   simulation. If some objects are too close together, this will ensure a noticeable gap   between them in the calculation of potentials and fields.
  * `for_weighting_potential::Bool = false`: Grid will be optimized for the calculation of    an [`ElectricPotential`](@ref) if set to `true`, and of a [`WeightingPotential`](@ref)   if set to `false`.
