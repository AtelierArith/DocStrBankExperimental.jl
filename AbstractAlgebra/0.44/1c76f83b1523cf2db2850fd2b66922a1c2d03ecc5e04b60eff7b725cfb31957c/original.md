```
swap_rows(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

Return a matrix $b$ with the entries of $a$, where the $i$th and $j$th row are swapped.

# Examples

```jldoctest
julia> M = identity_matrix(ZZ, 3)
[1   0   0]
[0   1   0]
[0   0   1]

julia> swap_rows(M, 1, 2)
[0   1   0]
[1   0   0]
[0   0   1]

julia> M  # was not modified
[1   0   0]
[0   1   0]
[0   0   1]
```
