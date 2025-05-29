```
partial_transpose(shadow::DenseShadow, subsystem::Vector{Int})::DenseShadow
```

Compute the partial transpose of a DenseShadow over the specified subsystem by swapping, for each site, the unprimed index with its primed partner. This is done using the `swapind` function, which returns a view of the underlying ITensor.

# Arguments

  * `shadow::DenseShadow`: The dense classical shadow.
  * `subsystem::Vector{Int}`: A vector of 1-based site indices on which to perform the partial transpose.

# Returns

A new DenseShadow with the specified sites partially transposed.
