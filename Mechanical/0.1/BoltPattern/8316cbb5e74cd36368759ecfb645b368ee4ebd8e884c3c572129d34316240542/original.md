```
rectangle(;x_dist, y_dist, Nx=2, Ny=2)
```

Compute the x & y coordinates of a rectangular bolt pattern.

`x_dist` is the width of the rectangular bolt pattern in the x-direction.  `y_dist` is the height of the rectangular bolt pattern in the y-direction.  `Nx` and `Ny` are the number of bolts along the width and height of the bolt pattern respectively. Units  conforming to the `Unitful` package should be applied.

# Examples

```julia-repl
julia> using Unitful: mm
julia> rectangle(x_dist = 250mm, y_dist = 125mm, Nx = 3, Ny=4)
(Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [-125.0 mm, -125.0 mm, -125.0 mm, -125.0 mm, 0.0 mm, 0.0 mm, 125.0 mm, 125.0 mm, 125.0 mm, 125.0 mm], Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [62.5 mm, 20.83333333333334 mm, -20.83333333333333 mm, -62.5 mm, 62.5 mm, -62.5 mm, 62.5 mm, 20.83333333333334 mm, -20.83333333333333 mm, -62.5 mm])
```
