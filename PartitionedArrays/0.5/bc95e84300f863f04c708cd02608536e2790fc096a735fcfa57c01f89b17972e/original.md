```
uniform_partition(ranks,np,n[,ghost[,periodic]])
```

Generate an `N` dimensional block partition of the indices in `LinearIndices(np)` with a (roughly) constant block size. The output is a vector of vectors containing the indices in each component of the partition. The `eltype` of the result implements the [`AbstractLocalIndices`](@ref) interface.

# Arguments

  * `ranks`: Array containing the distribution of ranks.
  * `np::NTuple{N}`: Number of parts per direction.
  * `n::NTuple{N}`: Number of global indices per direction.
  * `ghost::NTuple{N}=ntuple(i->false,N)`: Number of ghost indices per direction.
  * `periodic::NTuple{N}=ntuple(i->false,N)`: Use or not periodic boundaries per direction.

For convenience, one can also provide scalar inputs instead tuples to create 1D block partitions. In this case, the argument `np` can be omitted and it will be computed as `np=length(ranks)`. At the moment, it's only possible to use this syntax for zero (with `ghost=false`) or one (with `ghost=true`) layer(s) of ghost indices. If you wish to have more ghost indices, use tuples instead.

# Examples

2D partition of 4x4 indices into 2x2 parts without ghost

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((4,));

julia> uniform_partition(rank,10)
4-element Vector{PartitionedArrays.LocalIndicesWithConstantBlockSize{1}}:
 [1, 2]
 [3, 4]
 [5, 6, 7]
 [8, 9, 10]

julia> uniform_partition(rank,(2,2),(4,4))
4-element Vector{PartitionedArrays.LocalIndicesWithConstantBlockSize{2}}:
 [1, 2, 5, 6]
 [3, 4, 7, 8]
 [9, 10, 13, 14]
 [11, 12, 15, 16]
```
