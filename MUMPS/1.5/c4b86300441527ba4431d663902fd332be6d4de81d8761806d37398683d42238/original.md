```
solve(mumps, rhs; transposed=false)
```

Combined associate_rhs / solve. Presume that `rhs` is available on all nodes. The optional keyword argument `transposed` indicates whether the user wants to solve the forward or transposed system. The solution is retrieved and returned.
