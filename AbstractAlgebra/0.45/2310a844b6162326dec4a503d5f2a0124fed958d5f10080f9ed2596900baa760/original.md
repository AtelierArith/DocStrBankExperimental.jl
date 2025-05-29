```
is_diagonal(A::MatrixElem)
```

Return `true` if $A$ is a diagonal matrix, that is, all entries off the main diagonal are zero. Note that this definition also applies to non-square matrices.

Alias for `LinearAlgebra.isdiag`.

# Examples

```jldoctest
julia> is_diagonal(QQ[1 0 ; 0 4])
true

julia> is_diagonal(QQ[1 2 ; 3 4])
false

julia> is_diagonal(QQ[1 0 ;])
true
```
