```
axes2d(x_tick::Real, y_tick::Real, x_org::Real, y_org::Real, major_x::Int, major_y::Int, tick_size::Real)
```

Draw X and Y coordinate axes with linearly and/or logarithmically spaced tick marks.

**Parameters:**

`x_tick`, `y_tick` :     The interval between minor tick marks on each axis. `x_org`, `y_org` :     The world coordinates of the origin (point of intersection) of the X     and Y axes. `major_x`, `major_y` :     Unitless integer values specifying the number of minor tick intervals     between major tick marks. Values of 0 or 1 imply no minor ticks.     Negative values specify no labels will be drawn for the associated axis. `tick_size` :     The length of minor tick marks specified in a normalized device     coordinate unit. Major tick marks are twice as long as minor tick marks.     A negative value reverses the tick marks on the axes from inward facing     to outward facing (or vice versa).

Tick marks are positioned along each axis so that major tick marks fall on the axes origin (whether visible or not). Major tick marks are labeled with the corresponding data values. Axes are drawn according to the scale of the window. Axes and tick marks are drawn using solid lines; line color and width can be modified using the `setlinetype` and `setlinewidth` functions. Axes are drawn according to the linear or logarithmic transformation established by the `setscale` function.
