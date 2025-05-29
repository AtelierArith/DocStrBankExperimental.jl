```
rcef!(b::ZZ2Matrix; reduced = true) -> ZZ2Matrix
```

Return the tuple `(r, c)` where `r` is the rank of the matrix `b` and `c` a column echelon form of it. If `reduced` is `true`, then the reduced column echelon form is computed. The argument `b` may be modified during the computation, which avoids the allocation of a new matrix.

See also [`rcef`](@ref).
