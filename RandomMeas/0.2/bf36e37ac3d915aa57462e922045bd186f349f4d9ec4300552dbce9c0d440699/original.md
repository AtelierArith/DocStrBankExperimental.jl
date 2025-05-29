```
ComputationalBasisMeasurementSetting
```

A struct representing computational basis measurement settings for quantum systems. This setting uses the computational basis, so that each local unitary is by construction simply the identity operator.

# Fields

  * `N::Int`: Number of sites (qubits).
  * `local_unitary::Vector{ITensor}`: A vector of N identity ITensors.
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices (length N).

# Constraints

  * `N == length(site_indices)`.
