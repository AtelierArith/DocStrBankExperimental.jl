```
sparse_triangular_solve(LU::LU{F}, B::CSR{F})
sparse_triangular_solve(U::CSR{F}, B::CSR{F}, qinv::Vector{Int32})
```

Solve `X`*`LU.U` == `B`, respectively `X`*`U` = `B` in sparse matrices. The pivot positions of `U` are indicated in `qinv`.

Returns the solution `X` as a sparse matrix, or `nothing` if there is no solution.
