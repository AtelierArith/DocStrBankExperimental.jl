```
    exact_cover(matrix::Matrix{Bool}; do_check::Bool)
        matrix      `The incidence matrix`
        do_check    `Whether to check for invalid rows or columns.
                    (This will slow the execution time.)`
```

Initialize globals `incidence_matrix`, `nrows`, `ncols`.
