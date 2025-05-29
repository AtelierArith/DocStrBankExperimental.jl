```
transmutedims(A, perm⁺)
```

This is an eager version of [`transmute`](@ref), which always returns a `DenseArray`, but is not guaranteed to copy the data.

Like `transmute`, it knows to un-wrap `PermutedDimsArray`, `Transpose{<:Number}`, etc.

Like both `transmute` and [`TransmutedDimsArray`](@ref), it accepts in addition to perturbations, values outside `1:ndims(A)` (which insert trivial dimensions), omitted values (which like `dropdims` must be dimensions of size 1), and repeated values (which generalise `diagm`).

# Examples

```jldoctest; setup=:(using TransmuteDims)
julia> A = transmutedims(reshape(1:15,3,5), (3,2,1))  # A is a new Array
1×5×3 Array{Int64, 3}:
[:, :, 1] =
 1  4  7  10  13

[:, :, 2] =
 2  5  8  11  14

[:, :, 3] =
 3  6  9  12  15

julia> B = transmutedims(A, (2,3))  # drop A's first, trivial, dimension
5×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15

julia> C = transmutedims(adjoint(B), (2,1,0)); summary(C)  # un-wraps adjoint
"5×3×1 Array{Int64, 3}"

julia> D = transmutedims(adjoint(B), (1,0,2)); summary(D)  # unwraps, then permutes
"3×1×5 Array{Int64, 3}"

julia> B[5,3] = 5030;  # B and C are reshaped views of A

julia> A[1,5,3]
5030

julia> C[5,3,1]
5030

julia> D[3,1,5]  # but D is not, it required a copy
15

julia> transmutedims((1, 2, 3.0, 4+5im))  # default perm = (0,1) for vectors (and tuples)
1×4 Matrix{Number}:
 1  2  3.0  4+5im

julia> transmutedims(B)  # default perm = (2,1) for matrices
3×5 Matrix{Int64}:
 1  4  7  10    13
 2  5  8  11    14
 3  6  9  12  5030
```
