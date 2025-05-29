```
is_lower_triangular(A::MatrixElem)
```

Return `true` if $A$ is an lower triangular matrix, that is, all entries above the main diagonal are zero. Note that this definition also applies to non-square matrices.

Alias for `LinearAlgebra.istril`.

# Examples

```jldoctest
julia> is_lower_triangular(QQ[1 2 ; 0 4])
false

julia> is_lower_triangular(QQ[1 0 ; 3 4])
true

julia> is_lower_triangular(QQ[1 2 ;])
false

julia> is_lower_triangular(QQ[1 ; 2])
true
```
