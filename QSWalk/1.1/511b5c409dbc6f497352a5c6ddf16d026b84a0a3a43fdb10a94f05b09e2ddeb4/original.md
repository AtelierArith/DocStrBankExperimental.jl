```
default_nm_loc_ham(size)
```

Return default local Hamiltonian of size `size`×`size` for the demoralization procedure. The Hamiltonian is sparse with nonzero elements on the first upper diagonal (equal to `1im`) and lower diagonal (equal to `-1im`).

*Note:* This function is used to provide the default argument for `nm_loc_ham` function.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> QSWalk.default_nm_loc_ham(4)
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 6 stored entries:
  [2, 1]  =  0.0-1.0im
  [1, 2]  =  0.0+1.0im
  [3, 2]  =  0.0-1.0im
  [2, 3]  =  0.0+1.0im
  [4, 3]  =  0.0-1.0im
  [3, 4]  =  0.0+1.0im
```
