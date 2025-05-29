```julia
struct PlainMetisPartitioning <: ExtendableGrids.AbstractPartitioningAlgorithm
```

Subdivide grid into `npart` partitions using `Metis.partition` and color the resulting partition neighborhood graph. This requires to import Metis.jl in order to trigger the corresponding extension.

This algorithm allows to control  the overall number of partitions. The number of partitions per color comes from the subsequent partition graph coloring and in the moment cannot be controlled.

Parameters: 

  * `npart::Int64`: Number of partitions (default: 20)
