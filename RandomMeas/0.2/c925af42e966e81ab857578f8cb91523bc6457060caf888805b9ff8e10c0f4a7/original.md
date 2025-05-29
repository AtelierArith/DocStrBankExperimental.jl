```
ShallowUnitaryMeasurementSetting
```

A struct representing measurement settings which is, for each qubit, specified through a single qubit rotation, rotating from the computational basis into the measurement basis.

# Fields

  * `N::Int`: Number of sites (qubits).
  * 'K::Int`: Number of gates that creates the shallow_unitary
  * `localunitary::Vector{ITensor}`: A vector of Ngates representing the shallow unitary
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices of length N.

# Constructor

Creates a `ShallowUnitaryMeasurementSetting` object after validating that:

  * The length of `local_unitary` equals `K`
  * The length of `site_indices` equals `N`.
