```
fill_between(D1 [,D2]; kwargs...)
```

Fill the area between two horizontal curves.

The curves are defined by the points (x, y1, y2) in matrix or GMTdataset `D1`. This creates one or multiple polygons describing the filled area. Alternatively, give a second matrix, `D2` (or a scalar y=cte) and the polygons are constructed from the intersections of curves `D1` and `D2`.

  * `fill_between(..., fill=colors)`: Give a list with two colors to paint the 'up' and 'down' polygons.
  * `fill_between(..., fillalpha=[alpha1,alpha2])`: Sets the transparency of the two sets of polygons (default 60%).
  * `fill_between(..., pen=...)`: Sets pen specifications for the two curves. Easiest is to use the shortcuts  `lt`, `lc` and `ls` for the line thickness, color and style like it is used in the `plot()` module.
  * `fill_between(..., stairs=true)`: Plot stairs curves instead.
  * `fill_between(..., markers=true)`: Add marker points at the data locations.
  * `fill_between(..., white=true)`: Draw a thin white border between the curves and the fills.
  * `fill_between(..., labels=...)`: Pass labels to use in a legend.

      * `labels=true` wil use the column names in `D1` and `D2`.
      * `labels="Lab1,Lab2"` or `labels=["Lab1","Lab2"]` (this one can be a Tuple too) use the text in `Lab1`, `Lab2`.
  * `fill_between(..., legend=...)`: If used as the above `labels` it behaves like wise, but its argument can  also be a named tuple with `legend=(labels="Lab1,Lab2", position=poscode, box=(...))`.

Example:

```
theta = linspace(-2π, 2π, 150);
y1 = sin.(theta) ./ theta;
y2 = sin.(2*theta) ./ theta;
fill_between([theta y1], [theta y2], white=true, legend="Sinc1,Sinc2", show=1)
```
