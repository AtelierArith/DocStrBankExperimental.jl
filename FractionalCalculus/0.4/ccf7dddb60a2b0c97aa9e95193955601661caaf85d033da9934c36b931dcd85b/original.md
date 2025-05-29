# Grünwald Letnikov sense three point interpolation

```
fracdiff(f, α, end_point, h, GLLagrangeThreePointInterp())
```

Using Lagrange three poitns interpolation to approximate the fractional derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.006, GLLagrangeThreePointInterp())
1.1261297605404632
```
