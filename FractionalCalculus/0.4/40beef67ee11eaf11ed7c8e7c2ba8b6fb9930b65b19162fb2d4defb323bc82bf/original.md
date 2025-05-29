# Riesz sense symmetric fractional derivative algorithm.

```
fracdiff(f, α, end_point, h, RieszSymmetric())
```

Compute fractional derivative of Riesz sense using Triangular Strip Matrix algorithm.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, RieszSymmetric())
```
