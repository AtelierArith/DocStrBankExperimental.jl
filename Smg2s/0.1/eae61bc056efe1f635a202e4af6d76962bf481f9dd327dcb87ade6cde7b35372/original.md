```
Nilp(matrix::SparseMatrixCSC{Tv, Ti} ,size::Ti; maxdegree::Ti=80) where{Tv <: Real, Ti <: Integer}
```

Create a nilpotent matrix whose dimension is `size` from user-provided sparse matrix `matrix`. This matrix should be nilpotent, and its nilpotency should not be larger than `80`. Before generation, SMG2S.jl will check if the user-provided matrix is nilpotent matrix with nilpotency no larger than `80`. If it doesn't satisfy any of the two, an error message will appear.

## Examples

```jldoctest; setup = :(using SMG2S; using SparseArrays)
julia> nilpMatrix = sparse([0. 1 1 0; 0 0 1 1 ; 0 0 0 1 ; 0 0 0 0])
4×4 SparseMatrixCSC{Float64, Int64} with 5 stored entries:
  ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅

julia> SMG2S.Nilp(nilpMatrix,4)
┌ Info: the degree of given nilpotent matrix is:
└   degree = 4
Nilpotent{Int64}(1, 4, 4,
  ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅ )
```

## Examples

```julia
julia> nilpMatrix = sparse([1. 1 1 0; 0 0 1 1 ; 0 0 0 1 ; 0 0 0 0])
4×4 SparseMatrixCSC{Float64, Int64} with 6 stored entries:
 1.0  1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅

julia> SMG2S.Nilp(nilpMatrix,4)
ERROR: the given nilpotent matrix is invalid
```
