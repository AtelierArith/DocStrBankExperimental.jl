```
SymmetricPacked(A, uplo=:U)
```

Construct a `Symmetric` matrix in packed form of the upper (if `uplo = :U`) or lower (if `uplo = :L`) triangle of the matrix `A`.

# Examples

```jldoctest
julia> A = [1 0 2 0 3; 0 4 0 5 0; 6 0 7 0 8; 0 9 0 1 0; 2 0 3 0 4]
5×5 Matrix{Int64}:
 1  0  2  0  3
 0  4  0  5  0
 6  0  7  0  8
 0  9  0  1  0
 2  0  3  0  4

julia> AP = SymmetricPacked(A)
5×5 SymmetricPacked{Int64, Matrix{Int64}}:
 1  0  2  0  3
 0  4  0  5  0
 2  0  7  0  8
 0  5  0  1  0
 3  0  8  0  4

julia> Base.summarysize(A)
240

julia> Base.summarysize(AP)
184
```
