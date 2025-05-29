rq3 - RQ decomposition of 3x3 matrix

```
Usage:  R, Q = rq3(A)

Argument:  A - 3 x 3 matrix.
Returns:   R - Upper triangular 3 x 3 matrix
           Q - 3 x 3 orthonormal rotation matrix
               Such that  R*Q = A.
```

The signs of the rows and columns of R and Q are chosen so that the diagonal elements of R are +ve.

See also: decomposecamera()
