```
IMatrix{Tv}

IMatrix(n) -> IMatrix
IMatrix(A::AbstractMatrix{T}) where T -> IMatrix
```

Represents the Identity matrix with size `n`. `Int64` is its default type. Both `*` and `kron` are optimized.

# Example

```julia-repl
julia> IMatrix(4)
4×4 IMatrix{Bool}:
 1  0  0  0
 0  1  0  0
 0  0  1  0
 0  0  0  1

julia> IMatrix(rand(4,4))
4×4 IMatrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0

```
