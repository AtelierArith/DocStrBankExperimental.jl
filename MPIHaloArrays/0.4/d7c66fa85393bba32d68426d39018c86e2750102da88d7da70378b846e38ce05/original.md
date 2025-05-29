```
neighbor(p::CartesianTopology, i_offset::Int, j_offset::Int, k_offset::Int)
```

Find the neighbor rank based on the offesets in `(i,j,k)`. This follows the traditional array index convention rather than MPI's version, so an `i_offset=1` will shift up in the array indexing.

# Arguments

  * `p`: CartesianTopology type
  * `i_offset`: Offset in the `i` direction
  * `j_offset`: Offset in the `j` direction
  * `k_offset`: Offset in the `k` direction

# Example:

```julia
# Makes a 4x4 domain with periodic boundaries in both dimensions
P = CartesianTopology((4,4), (true, true))

# Find the ihi neighbor
ihi = neighbor(P,+1,0,0)

# Find the upper ihi corner neighbor (ihi and jhi side)
ihijhi_corner = neighbor(P,+1,+1,0)
```
