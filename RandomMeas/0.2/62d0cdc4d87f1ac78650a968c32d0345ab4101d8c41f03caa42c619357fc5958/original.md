```
flatten(O::Union{MPS, MPO, Vector{ITensor}})
```

Flatten a Matrix Product State (MPS), Matrix Product Operator (MPO), or a vector of ITensors into a single ITensor by sequentially multiplying the constituent tensors.

# Arguments

  * `O`: An MPS, MPO, or vector of ITensors to be flattened.

# Returns

An ITensor representing the product of the individual tensors in `O`.

# Example

```julia
A = random_mps(siteinds("Qubit", 5))
flatA = flatten(A)
```
