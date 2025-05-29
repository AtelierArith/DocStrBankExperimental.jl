```
partial_transpose(ρ::MPO, subsystem::Vector{Int})
```

Compute the partial transpose of an MPO over the sites specified by `subsystem`.

For each site index in the MPO:

  * If the index is in the `subsystem`, the tensor is transposed by swapping its unprimed and primed indices using `swapind`.
  * Otherwise, the tensor is left unchanged (multiplied by 1.0 for type consistency).

# Arguments

  * `ρ::MPO`: A Matrix Product Operator representing a density matrix.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) over which to apply the transpose.

# Returns

An MPO in which the tensors corresponding to the sites in `subsystem` have been partially transposed.

# Example

```julia
ρT = partial_transpose(ρ, [2, 3])
```
