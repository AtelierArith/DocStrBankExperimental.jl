```
lowerbd{T}(A::ReMat{T})
```

Return the vector of lower bounds on the parameters, `θ` associated with `A`

These are the elements in the lower triangle of `A.λ` in column-major ordering. Diagonals have a lower bound of `0`.  Off-diagonals have a lower-bound of `-Inf`.
