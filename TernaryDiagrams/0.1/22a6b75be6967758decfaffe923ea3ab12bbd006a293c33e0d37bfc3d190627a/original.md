TernaryContour

Draw a contour plot using barycentric coordindates, `x`, `y`, `z`, i.e. `x + y + z = 1`. The weight of the coordinates is passed through `w`. 

## Notes

  * `colormap` and `color` both apply to the color of the isolines. Thus, one of  them must be set to `nothing` to draw the correct coloredv isoclines.
  * `pad_data` adds extra data points for the purpose of generating prettier  isoclines. These padded points take the weight value of the closest actual  data point's weight.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{TernaryDiagrams.ternarycontour}` are: 

```
  clip_max_w  Inf
  clip_min_w  -Inf
  color       :black
  colormap    "nothing"
  levels      5
  linestyle   :solid
  linewidth   4
  pad_data    false
```
