```
apply(o::ITensor, ψ::Union{MPS, MPO}, [ns::Vector{Int}]; kwargs...)
product([...])
```

Get the product of the operator `o` with the MPS/MPO `ψ`, where the operator is applied to the sites `ns`. If `ns` are not specified, the sites are determined by the common indices between `o` and the site indices of `ψ`.

If `ns` are non-contiguous, the sites of the MPS are moved to be contiguous. By default, the sites are moved back to their original locations. You can leave them where they are by setting the keyword argument `move_sites_back` to false.

# Keywords

  * `cutoff::Real`: singular value truncation cutoff.
  * `maxdim::Int`: maximum MPS/MPO dimension.
  * `apply_dag::Bool = false`: apply the gate and the dagger of the gate (only  relevant for MPO evolution).
  * `move_sites_back::Bool = true`: after the ITensors are applied to the MPS or  MPO, move the sites of the MPS or MPO back to their original locations.
