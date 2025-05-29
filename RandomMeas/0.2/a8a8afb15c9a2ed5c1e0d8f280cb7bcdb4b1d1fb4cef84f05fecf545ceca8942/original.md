```
ShallowShadow
```

A struct representing a shallow classical shadow, stored as a MPO ITensor object.

# Fields

  * `shadow_data::MPOr`: An MPO representing the shallow shadow.
  * `N::Int`: Number of sites (qubits).
  * `site_indices::Vector{Index{Int64}}`: A vector of site indices (length N).

# Constructor

`ShallowShadow(shadow_data::MPO, N::Int, site_indices::Vector{Index{Int64}})` validates that:

  * `site_indices` has length N.
  * `shadow_data` has exactly N Tensors, and the site indices match with site_indices
