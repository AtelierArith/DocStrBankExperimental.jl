```
rcef(b::ZZ2Matrix; reduced = true) -> ZZ2Matrix
```

Return the tuple `(r, c)` where `r` is the rank of the matrix `b` and `c` a column echelon form of it. If `reduced` is `true`, then the reduced column echelon form is computed.

See also [`rref`](@ref), [`rcef!`](@ref).

# Examples

```jldoctest
julia> a = ZZ2Matrix([1 0 0; 1 1 1])
2×3 ZZ2Matrix:
 1  0  0
 1  1  1

julia> rcef(a)
(2, ZZ2[1 0 0; 0 1 0])

julia> rcef(a; reduced = false)
(2, ZZ2[1 0 0; 1 1 0])
```
