```
x = solve(F::LUFactor, rhs::Vector{Float64}, trans::Char) -> Vector{Float64}
```

Solve linear system with dense right-hand side. `rhs` is not modified. `trans` must be `'T'` for transposed solve or `'N'` for forward solve.
