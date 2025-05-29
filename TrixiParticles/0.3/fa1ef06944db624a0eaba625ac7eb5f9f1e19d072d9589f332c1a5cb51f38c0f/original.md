```
BoundaryModelLastiwka(; extrapolate_reference_values::Bool=false)
```

Boundary model for [`OpenBoundarySPHSystem`](@ref). This model uses the characteristic variables to propagate the appropriate values to the outlet or inlet and have been proposed by Lastiwka et al. (2009). It requires a specific flow direction to be passed to the [`BoundaryZone`](@ref). For more information about the method see [description below](@ref method_of_characteristics).

# Keywords

  * `extrapolate_reference_values=false`: If `true`, the reference values are extrapolated from the fluid domain to the boundary particles. This is useful for open boundaries where the reference values are not known a priori. **Note:** This feature is experimental and has not been fully validated yet. As of now, we are not aware of any published literature supporting its use.
