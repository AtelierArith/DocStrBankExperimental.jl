```
variable_partition(n_own,n_global[;start])
```

Build a 1D variable-size block partition of the range `1:n`. The output is a vector of vectors containing the indices in each component of the partition. The `eltype` of the result implements the [`AbstractLocalIndices`](@ref) interface.

# Arguments

  * `n_own::AbstractArray{<:Integer}`: Array containing the block size for each part.
  * `n_global::Integer`: Number of global indices. It should be equal to `sum(n_own)`.
  * `start::AbstractArray{Int}=scan(+,n_own,type=:exclusive,init=1)`: First global index in each part.

We ask the user to provide `n_global` and (optionally) `start` since discovering them requires communications.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((4,));

julia> n_own = [3,2,2,3];

julia> variable_partition(n_own,sum(n_own))
4-element Vector{PartitionedArrays.LocalIndicesWithVariableBlockSize{1}}:
 [1, 2, 3]
 [4, 5]
 [6, 7]
 [8, 9, 10]
```
