```
arrow(centerpos::Point, radius, startangle, endangle;
    linewidth          = 1.0,
    arrowheadlength    = 10,
    arrowheadangle     = π/8,
    decoration         = 0.5,
    decorate           = nothing,
    arrowheadfunction  = nothing,
    clockwise          = true)
```

Draw a curved arrow, an arc centered at `centerpos` starting at `startangle` and ending at `endangle` with an arrowhead at the end. Angles are measured clockwise from the positive x-axis.

Arrows don't use the current linewidth setting (`setline()`); you can specify the linewidth.

The `decorate` keyword argument accepts a zero-argument function that can execute code at one or more locations on the arrow's shaft. The inherited graphic environment is centered at points on the shaft between 0 and 1 given by scalar or vector `decoration`, and the x-axis is aligned with the direction of the curve at that point.

A triangular arrowhead is drawn by default. But you can pass a function to the `arrowheadfunction` keyword argument that accepts three arguments: the shaft end, the arrow head end, and the shaft angle. Thsi allows you to draw any shape arrowhead.
