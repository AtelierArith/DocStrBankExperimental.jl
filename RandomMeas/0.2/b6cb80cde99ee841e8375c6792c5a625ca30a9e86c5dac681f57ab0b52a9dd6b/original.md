```
LocalUnitaryMeasurementSetting(local_unitary_array; site_indices=nothing)
```

Create a `LocalUnitaryMeasurementSetting` object from an `N × 2 × 2` array of unitary matrices.

# Arguments:

  * `local_unitary_array::Array{ComplexF64, 3}`: An `N × 2 × 2` array of unitary matrices.
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}` (optional): Site indices. If `nothing`, they are automatically generated.

# Returns:

  * A `LocalUnitaryMeasurementSetting` object.

# Example:

```julia
unitary_array = rand(ComplexF64, 4, 2, 2)
setting = LocalUnitaryMeasurementSetting(unitary_array)
```
