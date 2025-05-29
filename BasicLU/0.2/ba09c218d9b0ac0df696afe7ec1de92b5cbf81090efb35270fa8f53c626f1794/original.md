```
solve!(F::LUFactor, rhs::Vector{Float64}, trans::Char) -> Vector{Float64}
```

Solve linear system with dense right-hand side. Solution overwrites `rhs`. `trans` must be `'T'` for transposed solve or `'N'` for forward solve.
