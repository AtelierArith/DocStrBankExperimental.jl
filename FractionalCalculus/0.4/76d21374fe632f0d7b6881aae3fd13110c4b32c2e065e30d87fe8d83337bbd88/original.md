# Atangana Baleanu sense fractional derivative computing using AtanganaSeda(Newton Polynomial) method.

```
fracdiff(f::Function, α, start_point, end_point, step_size, ::AtanganaSeda)
```

### Example:

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.0001, AtanganaSeda())
-91.4589645808849
```

### Reference

```tex
Fractional Stochastic Differential Equations
```
