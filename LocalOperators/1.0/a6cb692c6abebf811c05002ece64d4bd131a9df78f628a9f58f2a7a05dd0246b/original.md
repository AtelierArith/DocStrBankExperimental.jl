```
LocalOperator(A::AbstractMatrix, support::UnitRange{Int})
LocalOperator(A::AbstractMatrix, i::Int=0)
```

Contructs a `LocalOperator` corresponding to the matrix `A` with support on the indices  defined by the range `support`, or the single index `i` defaulting to `0`.
