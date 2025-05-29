```
struct PqPoints <: AbstractPqCurve
PqPoints(power_levels::Vector{Real}, discharge_levels::Vector{Real})
PqPoints(eq::Real)
```

The relationship between discharge/pumping of water and power generation/consumption represented by a set of discharge and power values (PQ-points).

## Fields

  * **`power_levels::Vector{Real}`** is a vector of power values.
  * **`discharge_levels::Vector{Real}`** is a vector of discharge values.

The two vectors muct be of equal size and ordered so that the power and discharge values describes the conversion from energy (stored in the water) to electricity (power) for a [`HydroGenerator`](@ref) node or the conversion from electric energy to energy stored as water in the reservoirs for a [`HydroPump`](@ref) node.

The first value in each vector should be zero. Furthermore, the vectors should be relative to the installed capacity, so that either the power-vector or the discharge vector is in the range [0, 1].

If a single `Real` is provided as input, it constructs the two Arrays through the energy equivalent input. If this approach is used, the installed capacity of the node must refer to the power capacity of a [`HydroGenerator`](@ref) or [`HydroPump`](@ref) node.

!!! note
    The described power-discharge relationship should be concave for a [`HydroGenerator`](@ref) node and convex for a [`HydroPump`](@ref) node.

