```
pma(A, G::AbstractMatrix{Bool}; nsv=6)
```

Computes the Principal Moment Analysis of the matrix `A` (variables × samples). Each column in `G` is a boolean vector representing one simplex. True means that a vertex is part of the simplex and false that it is not. Set `nsv` to control the number of singular values and vectors returned. Returns a `PMA` struct.

See also `PMA`, `SimplexGraph`.
