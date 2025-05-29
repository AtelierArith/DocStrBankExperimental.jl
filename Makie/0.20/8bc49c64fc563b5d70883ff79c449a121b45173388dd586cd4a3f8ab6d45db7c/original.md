```
bracket(x1, y1, x2, y2; kwargs...)
bracket(x1s, y1s, x2s, y2s; kwargs...)
bracket(point1, point2; kwargs...)
bracket(vec_of_point_tuples; kwargs...)
```

Draws a bracket between each pair of points (x1, y1) and (x2, y2) with a text label at the midpoint.

By default each label is rotated parallel to the line between the bracket points.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.bracket}` are: 

```
  align          (:center, :center)
  color          :black
  font           :regular
  fontsize       14
  justification  MakieCore.Automatic()
  linestyle      :solid
  linewidth      1.5
  offset         0
  orientation    :up
  rotation       MakieCore.Automatic()
  style          :curly
  text           ""
  textcolor      :black
  textoffset     MakieCore.Automatic()
  width          15
```
