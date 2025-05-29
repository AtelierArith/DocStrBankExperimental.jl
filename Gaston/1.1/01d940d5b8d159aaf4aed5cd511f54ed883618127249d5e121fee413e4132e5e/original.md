```
scatter(x, y [, axes] [, curve] ; args...) -> Gaston.Figure
```

Create a scatter plot with vectors `x` and `y`. `axes` and `curve` specify the axes and curve configurations, respectively.

```
scatter(c, args...) -> Gaston.Figure
```

If `c` is a complex vector, Create a scatter plot of the real and imaginary parts of `c`.
