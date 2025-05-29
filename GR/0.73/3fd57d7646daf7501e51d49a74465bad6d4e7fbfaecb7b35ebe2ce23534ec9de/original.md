```
fillarc(xmin::Real, xmax::Real, ymin::Real, ymax::Real, a1::Real, a2::Real)
```

Fill a circular or elliptical arc covering the specified rectangle.

**Parameters:**

`xmin` :     Lower left edge of the rectangle `xmax` :     Lower right edge of the rectangle `ymin` :     Upper left edge of the rectangle `ymax` :     Upper right edge of the rectangle `a1` :     The start angle `a2` :     The end angle

The resulting arc begins at `a1` and ends at `a2` degrees. Angles are interpreted such that 0 degrees is at the 3 o'clock position. The center of the arc is the center of the given rectangle.
