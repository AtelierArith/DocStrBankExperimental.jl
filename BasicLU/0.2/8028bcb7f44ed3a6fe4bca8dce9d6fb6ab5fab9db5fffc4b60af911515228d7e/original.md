```
solve!(F::LUFactor, rhs::SparseVector{Float64, Int64}, trans::Char) -> SparseVector{Float64, Int64}
```

Solve linear system with sparse right-hand side. Solution overwrites `rhs`. `trans` must be `'T'` for transposed solve or `'N'` for forward solve.
