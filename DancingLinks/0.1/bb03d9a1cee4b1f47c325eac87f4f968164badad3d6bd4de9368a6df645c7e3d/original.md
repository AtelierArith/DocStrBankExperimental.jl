```
    solve(starting_state::Vector{Int64}; verbose=false, max_solutions=1, deterministic=false) :: Bool
        starting_state      `List of rows by indices into the provided constraint matrix (global `incidence_matrix`)
                             that should be removed - they are "given" as part of the solution.`
        [verbose]           `Sets global `VERBOSE` flag; print timings.`
        [max_solutions]     `Sets global `SOLUTIONSMAX`; number of solutions to find before returning.`
        [deterministic]     `Sets global `DO_DETERMINISTICALLY; false=select rows at random.`
```

Solve the constraint matrix, global `incidence_matrix`.

Returns whether a solution was found or not.

You must have first set the global `incidence_matrix` with function `exact_cover()`.
