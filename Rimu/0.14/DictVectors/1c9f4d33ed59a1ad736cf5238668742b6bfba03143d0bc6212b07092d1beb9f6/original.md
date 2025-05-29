```
PDWorkingMemory(t::PDVec)
```

The working memory that handles threading and MPI distribution for operations that involve operators, such as FCIQMC propagation, operator-vector multiplication and three-way dot products with [`PDVec`](@ref)s.

The working memory is structured as a two-dimensional array of segments, which themselves are `Dict`s (see [`PDVec`](@ref)). The number of rows in this array is equal to the number of segments across all MPI ranks (covering the entire address space), while the number of columns corresponds to the number of segments in the current MPI rank (i.e. column corresponds to the part of the address space that is local to the current rank).

The purpose of this organisation is to allow spawning in parallel without using locks or atomic operations. The spawning is performed by applying the following sequence of operations:

  * [`perform_spawns!`](@ref): each segment in the [`PDVec`](@ref) is multiplied by the operator independently, with the results being stored in a column of the working memory.
  * [`collect_local!`](@ref): the rows of the working memory are summed to the first column.
  * [`synchronize_remote!`](@ref): the segments corresponding to other MPI ranks are distributed and transferred to the first column.
  * [`move_and_compress!`](@ref): the results are stochastically compressed and moved to the result [`PDVec`](@ref)

When used with three-argument dot products, a full copy of the left-hand side vector is materialized in the first column of the working memory on all ranks.
