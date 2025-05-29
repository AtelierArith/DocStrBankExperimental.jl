solveaffine - Solve affine transformation between two sets of 2D points.

```
Usage: A = solveaffine(xy1, xy2)

Arguments:
   xy1, xy2 - 2xN arrays of corresponding 2D points

Returns:
     A - 3x3 affine transformation matrix such that xy2 = A*xy1
         (assuming xy1 and xy2 are in homogeneous coords)

    [ x2        [ a  b  c    [ x1
      y2    =     d  e  f      y1
       1 ]        0  0  1 ]     1 ]

```
