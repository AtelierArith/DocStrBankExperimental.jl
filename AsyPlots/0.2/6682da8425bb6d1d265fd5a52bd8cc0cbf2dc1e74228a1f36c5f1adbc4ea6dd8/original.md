```
heatmap(A; colors)
heatmap(A, lowerleft, upperright; colors)
heatmap(xs, ys, f::Function)
```

Plot a heatmap of the values stored in the matrix `A`, using the colormap represented by the vector `colors` of `NamedColors`. Place the resulting `PixelMap` according to the given `lowerleft` and `upperright` tuples (which default to (0,0) and size(A)). 

# Examples

```julia-repl
julia> heatmap(0:10, 0:10, (x,y) -> x^2 + y^2)
```
