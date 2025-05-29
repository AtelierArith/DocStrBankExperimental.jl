```
DeltaArray(M::AbstractMatrix)
```

Constructs a matrix from the diagonal of `M`.

# Note

The resulting `DeltaArray` should in a similar way to a `Diagonal` object.

# Examples

```jldoctest julia> A = permutedims(reshape(1:15, 5, 3)) 3×5 Matrix{Int64}:   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15

julia> DeltaArray(A) 3×3 DeltaArray{Int64, 2, Vector{Int64}}:  1  0   0  0  7   0  0  0  13

julia> delta(A) 3-element Vector{Int64}:   1   7  13
