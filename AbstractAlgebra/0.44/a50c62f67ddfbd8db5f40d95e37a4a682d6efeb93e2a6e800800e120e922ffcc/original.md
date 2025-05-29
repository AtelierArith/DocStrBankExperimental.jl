```
is_upper_triangular(A::MatrixElem)
```

Return `true` if $A$ is an upper triangular matrix, that is, all entries below the main diagonal are zero. Note that this definition also applies to non-square matrices.

Alias for `LinearAlgebra.istriu`.

# Examples

```jldoctest
julia> is_upper_triangular(QQ[1 2 ; 0 4])
true

julia> is_upper_triangular(QQ[1 0 ; 3 4])
false

julia> is_upper_triangular(QQ[1 2 ;])
true

julia> is_upper_triangular(QQ[1 ; 2])
false
```
