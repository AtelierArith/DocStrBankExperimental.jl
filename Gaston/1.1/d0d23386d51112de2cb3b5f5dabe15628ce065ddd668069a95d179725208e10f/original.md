```
scatter3(x, y, z, [axes,] [curve,], args...) -> Gaston.Figure
```

Create a 3-D scatter plot with vectors `x`, `y` and `z`. `axes` and `curve` specify the axes and curve configurations, respectively.

```
scatter3(x, f1::Function, f2::Function, args...) -> Gaston.Figure
```

Create the scatter plot of `x`, `f1.(x)`, and `f2.(x)`.
