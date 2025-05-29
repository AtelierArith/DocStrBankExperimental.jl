```
grid(x_tick::Real, y_tick::Real, x_org::Real, y_org::Real, major_x::Int, major_y::Int)
```

Draw a linear and/or logarithmic grid.

**Parameters:**

`x_tick`, `y_tick` :     The length in world coordinates of the interval between minor grid     lines. `x_org`, `y_org` :     The world coordinates of the origin (point of intersection) of the grid. `major_x`, `major_y` :     Unitless integer values specifying the number of minor grid lines     between major grid lines. Values of 0 or 1 imply no grid lines.

Major grid lines correspond to the axes origin and major tick marks whether visible or not. Minor grid lines are drawn at points equal to minor tick marks. Major grid lines are drawn using black lines and minor grid lines are drawn using gray lines.
