```
neville(x, xₚ, yₚ)
```

Perform polynomial interpolation of the points defined by coordinates `xₚ` and values `yₚ`, at the coordinate `x`, using Neville's algorithm with as many points as are provided. `xₚ` and `yₚ` must have the same length. With only 3 or 4 points the [`quadratic`](@ref) and [`cubic`](@ref) functions will be considerably faster.
