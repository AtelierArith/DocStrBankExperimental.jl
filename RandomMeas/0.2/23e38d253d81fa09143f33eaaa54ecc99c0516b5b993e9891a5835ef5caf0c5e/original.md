```
FactorizedShadow
```

A struct representing a factorized classical shadow which can be represented as a tensor product of single qubit shadows.

# Fields

  * `shadow_data::Vector{ITensor}`: A vector of ITensors (each 2×2) representing the shadow for each qubit/site.
  * `N::Int`: Number of qubits/sites.
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices (length N).

# Constructor

`FactorizedShadow(shadow_data::Vector{ITensor}, N::Int, site_indices::Vector{Index{Int64}})` validates that:

  * The length of `shadow_data` and `site_indices` equals `N`.
  * Each ITensor in `shadow_data` has exactly two indices, which include the corresponding unprimed and primed site index.
