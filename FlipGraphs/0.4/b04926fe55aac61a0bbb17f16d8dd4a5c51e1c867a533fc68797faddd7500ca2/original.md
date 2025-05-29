```
matrix_equal(A::Matrix{Int}, B::Matrix{Int}) :: Bool
```

Return `true` if `A` equals `B`. 

This function is much faster than calling `A==B`. However, `A` and `B` are assumed to have the same dimensions.
