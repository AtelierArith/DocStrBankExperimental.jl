fitline3d - Fits a line to a set of 3D points

```
Usage:   L = fitline3d(XYZ)

Where: XYZ - 3xNpts array of XYZ coordinates
              [x1 x2 x3 ... xN;
               y1 y2 y3 ... yN;
               z1 z2 z3 ... zN]

Returns: L - 3x2 matrix consisting of the two endpoints of the line
             that fits the points.  The line is centered about the
             mean of the points, and extends in the directions of the
             principal eigenvectors, with scale determined by the
             eigenvalues.
```
