```
path(x, y, codes)
```

Draw paths using the given vertices and path codes.

**Parameters:**

`x` :     A list containing the X coordinates `y` :     A list containing the Y coordinates `codes` :     A list containing the path codes

The values for `x` and `y` are in world coordinates. The `codes` describe several path primitives that can be used to create compound paths.

The following path codes are recognized:

+–––––+––––––––––––––––-+–––––––––-+–––––––––-+ | **Code** | **Description**                 | **x**             | **y**             | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |     M, m | move                            | x                 | y                 | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |     L, l | line                            | x                 | y                 | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |     Q, q | quadratic Bezier                | x1, x2            | y1, y2            | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |     C, c | cubic Bezier                    | x1, x2, x3        | y1, y2, y3        | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |     A, a | arc                             | rx, a1, reserved  | ry, a2, reserved  | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |        Z | close path                      |                   |                   | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |        S | stroke                          |                   |                   | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |        s | close path and stroke           |                   |                   | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |        f | close path and fill             |                   |                   | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+ |        F | close path, fill and stroke     |                   |                   | +–––––+––––––––––––––––-+–––––––––-+–––––––––-+

  * Move: `M`, `m`

    Moves the current position to (`x`, `y`). The new position is either absolute (`M`) or relative to the current  position (`m`). The initial position of :code:`path` is (0, 0).

    Example:

    > > > path([0.5, -0.1], [0.2, 0.1], "Mm")


    The first move command in this example moves the current position to the absolute coordinates (0.5, 0.2). The  second move to performs a movement by (-0.1, 0.1) relative to the current position resulting in the point  (0.4, 0.3).

  * Line: `L`, `l`

    Draws a line from the current position to the given position (`x`, `y`). The end point of the line is either  absolute (`L`) or relative to the current position (`l`). The current position is set to the end point of the  line.

    Example:

    > > > path([0.1, 0.5, 0.0], [0.1, 0.1, 0.2], "MLlS")


    The first line to command draws a straight line from the current position (0.1, 0.1) to the absolute position  (0.5, 0.1) resulting in a horizontal line. The second line to command draws a vertical line relative to the  current position resulting in the end point (0.5, 0.3).

  * Quadratic Bezier curve: `Q`, `q`

    Draws a quadratic bezier curve from the current position to the end point (`x2`, `y2`) using (`x1`, `y1`) as the  control point. Both points are either absolute (`Q`) or relative to the current position (`q`). The current  position is set to the end point of the bezier curve.

    Example:

    > > > path([0.1, 0.3, 0.5, 0.2, 0.4], [0.1, 0.2, 0.1, 0.1, 0.0], "MQqS")


    This example will generate two bezier curves whose start and end points are each located at y=0.1. As the control  points are horizontally in the middle of each bezier curve with a higher y value both curves are symmetrical  and bend slightly upwards in the middle. The current position is set to (0.9, 0.1) at the end.

  * Cubic Bezier curve: `C`, `c`

    Draws a cubic bezier curve from the current position to the end point (`x3`, `y3`) using (`x1`, `y1`) and  (`x2`, `y2`) as the control points. All three points are either absolute (`C`) or relative to the current position  (`c`). The current position is set to the end point of the bezier curve.

    Example:

    > > > path(


    ...     [0.1, 0.2, 0.3, 0.4, 0.1, 0.2, 0.3],  ...     [0.1, 0.2, 0.0, 0.1, 0.1, -0.1, 0.0],  ...     "MCcS"  ... )

    This example will generate two bezier curves whose start and end points are each located at y=0.1. As the control  points are equally spaced along the x-axis and the first is above and the second is below the start and end  points this creates a wave-like shape for both bezier curves. The current position is set to (0.8, 0.1) at the  end.

  * Ellipctical arc: `A`, `a`

    Draws an elliptical arc starting at the current position. The major axis of the ellipse is aligned with the x-axis  and the minor axis is aligned with the y-axis of the plot. `rx` and `ry` are the ellipses radii along the major  and minor axis. `a1` and `a2` define the start and end angle of the arc in radians. The current position is set  to the end point of the arc. If `a2` is greater than `a1` the arc is drawn counter-clockwise, otherwise it is  drawn clockwise. The `a` and `A` commands draw the same arc. The third coordinates of the `x` and `y` array are  ignored and reserved for future use.

    Examples:

> > > path([0.1, 0.2, -3.14159 / 2, 0.0], [0.1, 0.4, 3.14159 / 2, 0.0], "MAS")


This example draws an arc starting at (0.1, 0.1). As the start angle -pi/2 is smaller than the end angle pi/2 the    arc is drawn counter-clockwise. In this case the right half of an ellipse with an x radius of 0.2 and a y radius    of 0.4 is shown. Therefore the current position is set to (0.1, 0.9) at the end.

> > > path([0.1, 0.2, 3.14159 / 2, 0.0], [0.9, 0.4, -3.14159 / 2, 0.0], "MAS")


This examples draws the same arc as the previous one. The only difference is that the starting point is now at    (0.1, 0.9) and the start angle pi/2 is greater than the end angle -pi/2 so that the ellipse arc is drawn    clockwise. Therefore the current position is set to (0.1, 0.1) at the end.

  * Close path: `Z`

    Closes the current path by connecting the current position to the target position of the last move command  (`m` or `M`) with a straight line. If no move to was performed in this path it connects the current position to  (0, 0). When the path is stroked this line will also be drawn.

  * Stroke path: `S`, `s`

    Strokes the path with the current border width and border color (set with :code:`gr.setborderwidth` and  :code:`gr.setbordercolorind`). In case of `s` the path is closed beforehand, which is equivalent to `ZS`.

  * Fill path: `F`, `f`

    Fills the current path using the even-odd-rule using the current fill color. Filling a path implicitly closes  the path. The fill color can be set using :code:`gr.setfillcolorind`. In case of `F` the path is also  stroked using the current border width and color afterwards.
