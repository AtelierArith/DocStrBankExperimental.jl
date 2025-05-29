```
GateIndex
```

An object that stores all of the different indices of a gate.

# Fields

  * `gate::Gate`: The gate.
  * `indices::Vector{Int32}`: Gate eigenvalue or probability indices.
  * `pad_indices::Vector{Int32}`: Padded gate eigenvalue or probability indices.
  * `marg_indices::Vector{Int32}`: Marginal gate eigenvalue or probability indices.
  * `pad_marg_indices::Vector{Int32}`: Padded marginal gate eigenvalue or probability indices.
  * `rel_indices::Vector{Int32}`: Relative gate eigenvalue or probability indices.
  * `pad_rel_indices::Vector{Int32}`: Padded relative gate eigenvalue or probability indices.
