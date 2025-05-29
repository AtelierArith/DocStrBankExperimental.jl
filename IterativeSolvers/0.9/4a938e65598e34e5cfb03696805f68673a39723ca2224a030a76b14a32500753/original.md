```
lobpcg!(iterator::LOBPCGIterator; kwargs...) -> results
```

# Arguments

  * `iterator::LOBPCGIterator`: a struct having all the variables required   for the LOBPCG algorithm.

## Keywords

  * `not_zeros`: default is `false`. If `true`, the initial Ritz vectors will be assumed to not have any all-zeros column.
  * `log::Bool`: default is `false`; if `true`, `results.trace` will store iterations   states; if `false` only `results.trace` will be empty;
  * `maxiter`: maximum number of iterations; default is 200;
  * `tol::Real`: tolerance to which residual vector norms must be under.

# Output

  * `results`: a `LOBPCGResults` struct. `r.λ` and `r.X` store the eigenvalues and eigenvectors.
