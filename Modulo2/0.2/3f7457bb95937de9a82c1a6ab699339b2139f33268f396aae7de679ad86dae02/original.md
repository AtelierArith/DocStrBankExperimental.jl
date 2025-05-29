```
rref(b::ZZ2Matrix; reduced = true) -> ZZ2Matrix
```

Return the tuple `(r, c)` where `r` is the rank of the matrix `b` and `c` a row echelon form of it. If `reduced` is `true`, then the reduced row echelon form is computed.

Note that it is more efficient to compute a (reduced) *column* echelon form via `rcef`.

See also [`rcef`](@ref).

# Examples

```jldoctest
julia> a = ZZ2Matrix([1 1; 0 1; 0 1])
3×2 ZZ2Matrix:
 1  1
 0  1
 0  1

julia> rref(a)
(2, ZZ2[1 0; 0 1; 0 0])

julia> rref(a; reduced = false)
(2, ZZ2[1 1; 0 1; 0 0])
```
