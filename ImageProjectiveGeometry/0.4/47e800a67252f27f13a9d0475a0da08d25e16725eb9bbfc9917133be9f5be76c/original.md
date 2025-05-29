fitline2d - Least squares fit of a line to a set of 2D points

```
Usage:   (C, dist) = fitline2d(XY)

Where:   XY  - 2xNpts array of xy coordinates to fit line to data of
               the form
               [x1 x2 x3 ... xN
                y1 y2 y3 ... yN]

               XY can also be a 3xNpts array of homogeneous coordinates.

Returns: C    - 3x1 array of line coefficients in the form
                c[1]*X + c[2]*Y + c[3] = 0
         dist - Array of distances from the fitted line to the supplied
                data points.  Note that dist is only calculated if the
                function is called with two output arguments.
```

The magnitude of C is scaled so that line equation corresponds to

```
   sin(theta)*X + (-cos(theta))*Y + rho = 0
```

where theta is the angle between the line and the x axis and rho is the perpendicular distance from the origin to the line.  Rescaling the coefficients in this manner allows the perpendicular distance from any point (x,y) to the line to be simply calculated as

```
   r = abs(c[1]*X + c[2]*Y + c[3])
```

If you want to convert this line representation to the classical form

```
     Y = a*X + b
use
  a = -c[1]/c[2]
  b = -c[3]/c[2]
```

Note, however, that this assumes c[2] is not zero
