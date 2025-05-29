```
bound_perron_frobenius_eigenvalue(A, max_iter=10)
```

Finds an upper bound for the Perron-Frobenius eigenvalue of the **non-negative** matrix `A`.

### Input

  * `A` – square real non-negative matrix
  * `max_iter` – maximum number of iterations of the power method used internally to compute   an initial approximation of the Perron-Frobenius eigenvector

### Example

```julia-repl
julia> A = [1 2;3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> bound_perron_frobenius_eigenvalue(A)
5.372281323275249
```
