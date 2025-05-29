```
LocalUnitaryMeasurementSetting(N, local_unitary, site_indices)
```

A measurement setting where each qubit is specified by a single-qubit rotation. Rotates from the computational basis into the measurement basis.

# Fields

  * `N::Int`: Number of sites (qubits).
  * `local_unitary::Vector{ITensor}`: A vector of `N` ITensors representing the local unitary basis rotations.
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices of length `N`.

# Constraints

  * `N == length(local_unitary) == length(site_indices)`.
  * Each ITensor in `local_unitary` has exactly **two indices**:

      * One unprimed (`site_indices[i]`)
      * One primed (`prime(site_indices[i])`).
