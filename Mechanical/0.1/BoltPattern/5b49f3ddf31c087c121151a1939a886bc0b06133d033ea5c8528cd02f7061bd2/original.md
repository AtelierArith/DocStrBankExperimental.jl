```
circle(;r, N=4, theta_start=0)
```

Compute the x & y coordinates of a circular bolt pattern.

`r` is the radius of the bolt pattern and `N` is the number of bolts in the bolt pattern.  `theta_start` is the angle measured clockwise from the y-axis to the first bolt in the pattern. Units  conforming to the `Unitful` package should be applied.

# Examples

```julia-repl
julia> using Unitful: mm
julia> circle(r=100mm, N=3)
(Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [6.123233995736766e-15 mm, 86.60254037844386 mm, -86.60254037844388 mm], Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [100.0 mm, -50.0 mm, -49.99999999999999 mm])
```
