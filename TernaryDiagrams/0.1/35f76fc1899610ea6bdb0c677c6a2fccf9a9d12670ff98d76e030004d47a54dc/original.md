TernaryContourf

Draw a filled contour plot using barycentric coordindates, `x`, `y`, `z`, i.e. `x + y + z = 1`. The weight of the coordinates is passed through `w`.

## Notes

The data is always padded to make filling the entire plot area easier. Padded data is interpolated based on the nearest data point.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{TernaryDiagrams.ternarycontourf}` are: 

```
  colormap  :Spectral
  levels    5
```
