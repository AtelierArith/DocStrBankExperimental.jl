```
surf([x,] [y,] z, [axes,] args...)-> Gaston.Figure
```

Plot the surface specified by `z` with axes specification `axes`.

```
surf(x, y f::Function, args...)-> Gaston.Figure
```

Plot the surface `f.(x,y)`.
