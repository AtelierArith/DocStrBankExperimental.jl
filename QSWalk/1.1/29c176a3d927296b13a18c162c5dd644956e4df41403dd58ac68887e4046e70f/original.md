```
local_lind(A[; epsilon])
```

Split the elements of the matrix `A` into a collection of sparse matrices with exactly one non-zero element. Martices are created if the absolute value of the nonzero element is there are not smaller than `epsilon`, where `epsilon` should be nonnegative. The `epsilon` defaults to `eps()` if not specified.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> A = [1. 2.; 3. 4.]
2×2 Array{Float64,2}:
 1.0  2.0
 3.0  4.0

julia> local_lind(A)
4-element Array{SparseArrays.SparseMatrixCSC{Float64,Ti} where Ti<:Integer,1}:

  [1, 1]  =  1.0

  [1, 2]  =  2.0

  [2, 1]  =  3.0

  [2, 2]  =  4.0

julia> local_lind(A, epsilon = 1.5)
3-element Array{SparseArrays.SparseMatrixCSC{Float64,Ti} where Ti<:Integer,1}:

  [1, 2]  =  2.0

  [2, 1]  =  3.0

  [2, 2]  =  4.0

```
