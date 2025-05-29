# Riemann Liouville sense derivative approximation

```
fracdiff(f, α, end_point, h, RLDiffL1())
```

Using the L1 algorithm Linear interpolation to approximate fractional derivative in Riemann Liouville  fractional derivative sense.

### Example

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.0001, RLDiffL1())
141.59707906952633
```

!!! warning
    The RLDiffL1 algorithm only support for 0 < α < 1.

