```
    solve(; verbose=false, max_solutions=1, deterministic=false) :: Bool
        [verbose]         `Sets global `VERBOSE` flag; print timings, etc.`
        [max_solutions]   `Sets global `SOLUTIONSMAX`; number of solutions to find before returning.`
        [deterministic]   `Sets global `DO_DETERMINISTICALLY; false=select rows at random.`
```

Solve the constraint matrix, global `incidence_matrix`.Solve with no givens.

Returns whether a solution was found or not.

This is useful when the matrix provided in global `incidence_matrix` is the actual matrix (ie. there are no `givens`).
