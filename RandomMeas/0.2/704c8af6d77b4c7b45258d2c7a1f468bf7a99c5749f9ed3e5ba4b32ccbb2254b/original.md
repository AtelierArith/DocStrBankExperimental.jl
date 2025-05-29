```
DenseShadow
```

A struct representing a dense classical shadow (a 2^N x 2^N matrix), stored as a single ITensor with 2N indices.

# Fields

  * `shadow_data::ITensor`: An ITensor with 2N indices representing the dense shadow.
  * `N::Int`: Number of sites (qubits).
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices (length N).

# Constructor

`DenseShadow(shadow_data::ITensor, N::Int, site_indices::Vector{Index{Int64}})` validates that:

  * `site_indices` has length N.
  * `shadow_data` has exactly 2N indices.
  * The set of unprimed indices in `shadow_data` matches `site_indices`.
  * The set of primed indices in `shadow_data` matches `map(prime, site_indices)`.
