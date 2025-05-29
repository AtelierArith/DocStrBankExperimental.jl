```
isolines(xs, ys, zs; lift = false, interpolation = :cubic)
```

Plot the contour lines of the function whose values are represented by the array (or function) `zs`. If `lift` is true, plot in 3D.

# Examples

```julia-repl julia> isolines(0:10, 0:10, (x,y) -> (100 - x^2 + y^2)/10, lift = true)
