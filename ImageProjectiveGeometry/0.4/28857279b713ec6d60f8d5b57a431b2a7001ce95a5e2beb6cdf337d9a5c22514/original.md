fitplane - Solves coefficients of plane fitted to 3 or more points

```
Usage:   B = fitplane(XYZ)

Where:   XYZ - 3xNpts array of xyz coordinates to fit plane to.
               If Npts is greater than 3 a least squares solution
               is generated.

Returns: B   - 4x1 array of plane coefficients in the form
               B[1]*X + B[2]*Y + B[3]*Z + B[4] = 0
               The magnitude of B is 1.
```

See also: ransacfitplane()
