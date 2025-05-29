```
contour([x,] [y,] z::Matrix, labels = true, [axes,] args...) -> Gaston.Figure
```

Plot the contour lines given by the surface `z`. If `labels = false`, no labels are included in the plot.

```
contour(x, y, f::Function, args...) -> Gaston.Figure
```

Plot the contours of the surface `f.(x,y)`.
