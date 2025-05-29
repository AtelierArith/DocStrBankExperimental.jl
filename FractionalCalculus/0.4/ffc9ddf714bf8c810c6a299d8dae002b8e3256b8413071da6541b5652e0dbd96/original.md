# Riemann Liouville sense fractional integral using **Linear interpolation**.

```
fracint(f, α, end_point, h, RLLinearInterp())
```

### Example

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLLinearInterp())
64.36234206434942
```

**RLLinearInterp** is more complex compared with *RLIntApprox* but more precise.

Deploying the [Linear Interpolation](https://en.wikipedia.org/wiki/Linear_interpolation) between $f_{j+1}$ and $f_j$, **RLLinearInterp** method is more precise than **RLIntApprox**.
