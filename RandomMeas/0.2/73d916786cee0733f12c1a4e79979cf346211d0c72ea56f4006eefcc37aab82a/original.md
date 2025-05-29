```
ComputationalBasisMeasurementSetting(N; site_indices=nothing)
```

Create a `ComputationalBasisMeasurementSetting` for `N` sites. This setting corresponds to measurement in the computational basis.

# Arguments:

  * `N::Int`: Number of sites (qubits).
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}` (optional): Site indices. If `nothing`, they are automatically generated.

# Returns:

  * A `ComputationalBasisMeasurementSetting` object.

# Example:

```julia
setting = ComputationalBasisMeasurementSetting(4)
```
