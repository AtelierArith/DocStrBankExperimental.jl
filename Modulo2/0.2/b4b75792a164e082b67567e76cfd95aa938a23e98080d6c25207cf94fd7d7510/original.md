```
inv!(b::ZZ2Matrix) -> ZZ2Matrix
```

Return the inverse of the matrix `b`, which must be invertible. The argument `b` may be modified during the computation, which avoids the allocation of a new matrix.

See also [`inv`](@ref).
