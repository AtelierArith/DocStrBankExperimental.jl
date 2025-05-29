```
get_z(c::Surface) -> z::Matrix{Float64}
```

Return the matrix of `z` values for surface `c`. `z[i,j]` is the $z$ value sampled at $(x, y)$ coordinates $($`x[i]`, `y[j]`$)$.
