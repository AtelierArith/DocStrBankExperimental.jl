```
ShallowUnitaryMeasurementSetting(N, depth; site_indices=nothing)
```

Create a `ShallowUnitaryMeasurementSetting` object by generating a random quantum circuit.

# Arguments:

  * `N::Int`: Number of sites (qubits).
  * `depth::Int`: Depth of the random circuit.
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}` (optional): Site indices. If `nothing`, they are automatically generated.

# Returns:

  * A `ShallowUnitaryMeasurementSetting` object.

# Example:

```julia
setting = ShallowUnitaryMeasurementSetting(4, 3)
```
