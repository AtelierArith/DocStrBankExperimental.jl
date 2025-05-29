```
fourier_matrix(size)
```

Returns Fourier matrix of size `size`×`size`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> fourier_matrix(1)
1×1 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 1 stored entry:
  [1, 1]  =  1.0+0.0im

julia> fourier_matrix(2)
2×2 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 4 stored entries:
  [1, 1]  =  1.0+0.0im
  [2, 1]  =  1.0+0.0im
  [1, 2]  =  1.0+0.0im
  [2, 2]  =  -1.0+1.22465e-16im

```
