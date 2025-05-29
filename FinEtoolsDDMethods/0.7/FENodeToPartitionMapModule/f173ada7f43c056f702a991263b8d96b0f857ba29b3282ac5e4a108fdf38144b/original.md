```
FENodeToPartitionMap(n2e::N2EMAP, element_partitioning::Vector{IT}) where {N2EMAP<:FENodeToFEMap,N,IT<:Integer}
```

Map from finite element nodes to the partitions to which they belong.

# Arguments

  * `n2e::N2EMAP`: A mapping between finite element nodes and finite elements.
  * `element_partitioning::Vector{IT}`: A vector specifying the partitioning of elements.
