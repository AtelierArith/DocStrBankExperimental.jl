```
LocalUnitaryMeasurementSetting(N; site_indices=nothing, ensemble="Haar")
```

Create a `LocalUnitaryMeasurementSetting` object by randomly sampling local unitary operators.

# Arguments:

  * `N::Int`: Number of sites (qubits).
  * `site_indices::Union{Vector{Index}, Nothing}` (optional): Site indices. If `nothing`, they are automatically generated.
  * `ensemble::String`: Type of random unitary (`"Haar"`, `"Pauli"`, `"Identity"`).

# Returns:

  * A `LocalUnitaryMeasurementSetting` object.

# Example:

```julia
setting = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
```
