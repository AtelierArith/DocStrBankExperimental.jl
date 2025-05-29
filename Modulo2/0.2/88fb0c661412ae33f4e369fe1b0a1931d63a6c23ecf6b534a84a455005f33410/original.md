```
rank!(b::ZZ2Matrix) -> Int
```

Return the rank of the matrix `b`. The argument `b` may be modified during the computation, which avoids the allocation of a new matrix.

See also [`rank`](@ref).
