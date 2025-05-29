```
spy(M::AbstractMatrix, elements::ElementOrFunction...; mapping...) -> Plot
```

Plots a heatmap of `M`, with M[1,1] in the upper left.  `NaN` values are left blank, and an error is thrown if all elements of `M` are `NaN`.  See [`Geom.rectbin`](@ref) and [`Coord.cartesian(fixed=true)...)`](@ref Gadfly.Coord.cartesian).
