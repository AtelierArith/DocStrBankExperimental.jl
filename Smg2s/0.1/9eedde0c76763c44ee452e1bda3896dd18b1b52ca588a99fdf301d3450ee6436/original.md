```
nonherm(nbOne::Ti, size::Ti, diag_l::Ti, diag_u::Ti, spectrum::AbstractVector{Tv}, Am::SparseMatrixCSC{Tv, Ti}) where {Tv<:Complex, Ti<:Integer}
```

Generate a non hermitian matrix with default nilpotent matrix and user-provided initialization of matrix.

## Examples

```julia
julia> spec=[1+im, 2, 4, 6, 7-2im, 4+3im, 7, 8, 9, 10.2-im]
10-element Vector{ComplexF64}:
  1.0 + 1.0im
  2.0 + 0.0im
  4.0 + 0.0im
  6.0 + 0.0im
  7.0 - 2.0im
  4.0 + 3.0im
  7.0 + 0.0im
  8.0 + 0.0im
  9.0 + 0.0im
 10.2 - 1.0im

julia> Am = spzeros(ComplexF64, 10, 10);
julia> initMat!(Am, -8, -2, 10; scale=0.1, sparsity=0.005)
julia> nonherm(3, 10, -8, -2, spec, Am)
10×10 SparseMatrixCSC{ComplexF64, Int64} with 22 stored entries:
 1.0+1.0im  -0.5+0.5im  0.0833333+0.0833333im  0.00347222+0.00347222im      ⋅          ⋅           ⋅                     ⋅                ⋅           ⋅
     ⋅       2.0+0.0im       -1.0+0.0im                   ⋅                 ⋅          ⋅           ⋅                     ⋅                ⋅           ⋅
     ⋅           ⋅            4.0+0.0im              -1.0+0.0im             ⋅          ⋅           ⋅                     ⋅                ⋅           ⋅
     ⋅           ⋅                ⋅                   6.0+0.0im             ⋅          ⋅           ⋅                     ⋅                ⋅           ⋅
     ⋅           ⋅                ⋅                       ⋅             7.0-2.0im  1.5-2.5im   0.5-0.666667im  0.0277778-0.0381944im      ⋅           ⋅
     ⋅           ⋅                ⋅                       ⋅                 ⋅      4.0+3.0im  -1.5+1.5im       -0.166667+0.25im           ⋅           ⋅
     ⋅           ⋅                ⋅                       ⋅                 ⋅          ⋅       7.0+0.0im            -0.5+0.0im            ⋅           ⋅
     ⋅           ⋅                ⋅                       ⋅                 ⋅          ⋅           ⋅                 8.0+0.0im            ⋅           ⋅
     ⋅           ⋅                ⋅                       ⋅                 ⋅          ⋅           ⋅                     ⋅            9.0+0.0im  -0.6+0.5im
     ⋅           ⋅                ⋅                       ⋅                 ⋅          ⋅           ⋅                     ⋅                ⋅      10.2-1.0im
```
