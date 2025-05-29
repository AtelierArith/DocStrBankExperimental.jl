```
MeasurementProbability{T}

A container for measurement probabilities and settings obtained either estimated from measurement data or directly computed from quantum states.
```

# Fields

  * `N::Int`: Number of sites (qubits).
  * `measurement_probability::ITensor`: An ITensor representing Born probability.
  * `measurement_setting::T`: A measurement setting of type `T` or `nothing`.
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices (length N).

# Type Parameter

  * `T`: The type of measurement setting, constrained to `Union{Nothing, AbstractMeasurementSetting}`.

# Usage

Constructed either from measurement data or directly from quantum states.
