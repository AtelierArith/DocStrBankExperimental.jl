```
solve(mumps, A, rhs; transposed=false)
```

Combined analyze / factorize / solve. Presume that `A` and `rhs` are available on all nodes. The optional keyword argument `transposed` indicates whether the user wants to solve the forward or transposed system. The solution is retrieved and returned.
