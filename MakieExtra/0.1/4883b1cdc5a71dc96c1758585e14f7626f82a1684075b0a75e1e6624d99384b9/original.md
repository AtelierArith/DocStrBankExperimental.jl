```
zoom_lines!(ax1, ax2; strokewidth=1.5, strokecolor=:black, color=(:black, 0), rectattrs=(;), lineattrs=(;))
```

Draws:

  * a rectangle on axis that has larger limits outlining the smaller limits of the other axis;
  * lines connecting corresponding corners of the rectangles.

Common attributes shared by both rectangles and lines are `strokewidth` and `strokecolor`. `rectattrs` and `lineattrs` are used to override the attributes of the rectangles and lines separately when needed.
