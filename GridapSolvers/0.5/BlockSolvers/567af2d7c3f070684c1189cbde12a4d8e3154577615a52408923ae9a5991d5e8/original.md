```
struct BlockDiagonalSolver{N} <: LinearSolver
```

Solver representing a block-diagonal solver, i.e 

```
│ A11   0    0  │   │ x1 │   │ r1 │
│  0   A22   0  │ ⋅ │ x2 │ = │ r2 │
│  0    0   A33 │   │ x3 │   │ r3 │
```

where `N` is the number of diagonal blocks.

# Properties:

  * `blocks::AbstractVector{<:SolverBlock}`: Matrix of solver blocks, indicating how    each diagonal block of the preconditioner is obtained.
  * `solvers::AbstractVector{<:LinearSolver}`: Vector of solvers,    one for each diagonal block.
