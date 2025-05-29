```julia
struct RecursiveMetisPartitioning <: ExtendableGrids.AbstractPartitioningAlgorithm
```

Subdivide grid into `npart` partitions using `Metis.partition` and calculate cell separators from this partitioning. The initial partitions  get color 1, and the separator gets color 2. This is continued recursively with partitioning of the separator into `npart` partitions and calculating the separator of the separator, giving it color 3.

This algorithm allows to control  the number of partitions in color 1 which correspond to the bulk of the work. The overall number of partitions will be in the range of `3*npart`.

If the grid is too coarse for that many partitions, several of them may be just empty.

Parameters: 

  * `npart::Int64`: Number of color 1 partitions (default: 4)
  * `maxdepth::Int64`: Recursion depth (default: 1)
  * `separatorwidth::Int64`: Separator width  (default: 2)
