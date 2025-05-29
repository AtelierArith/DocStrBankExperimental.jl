```
det!(b::ZZ2Matrix) -> ZZ2
```

Return the determinant of the matrix `b`. The argument `b` may be modified during the computation, which avoids the allocation of a new matrix.

See also [`det`](@ref).
