```
solve!(mumps;transposed=false)
```

Solve the system registered with the `Mumps` object `mumps`. The matrix and right-hand side(s) must have been previously registered with `associate_matrix()` and `associate_rhs()`. The optional keyword argument `transposed` indicates whether the user wants to solve the forward or transposed system. The solution is stored internally and must be retrieved with `get_solution()`.
