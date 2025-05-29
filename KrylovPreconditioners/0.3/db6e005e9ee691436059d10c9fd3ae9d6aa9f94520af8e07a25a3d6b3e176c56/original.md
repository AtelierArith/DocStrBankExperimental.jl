```
BlockJacobiPreconditioner
```

Overlapping-Schwarz preconditioner.

### Attributes

  * `nblocks::Int64`: Number of partitions or blocks.
  * `blocksize::Int64`: Size of each block.
  * `partitions::Vector{Vector{Int64}}``:`npart` partitions stored as lists
  * `cupartitions`: `partitions` transfered to the GPU
  * `lpartitions::Vector{Int64}``: Length of each partitions.
  * `culpartitions::Vector{Int64}``: Length of each partitions, on the GPU.
  * `blocks`: Dense blocks of the block-Jacobi
  * `cublocks`: `Js` transfered to the GPU
  * `map`: The partitions as a mapping to construct views
  * `cumap`: `cumap` transferred to the GPU`
  * `part`: Partitioning as output by Metis
  * `cupart`: `part` transferred to the GPU
