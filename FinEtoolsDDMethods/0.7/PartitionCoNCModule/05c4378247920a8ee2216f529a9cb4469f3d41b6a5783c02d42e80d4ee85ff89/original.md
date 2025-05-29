```
CoNCPartitionData(cpi::CPI, 
rank, 
fes, 
make_matrix, 
make_interior_load = nothing
) where {CPI<:CoNCPartitioningInfo}
```

Create partition data.

# Arguments

  * `cpi`: partitioning info
  * `rank`: rank of the partition, zero based
  * `fes`: finite element set
  * `make_matrix`: function that creates the matrix for a given finite element subset
  * `make_interior_load`: function that creates the interior load vector for a given finite element subset
