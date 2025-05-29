homotrans - Homogeneous transformation of points/lines

Function to perform a transformation on 2D or 3D homogeneous or inhomogeneous coordinates. The resulting coordinates are normalised to have a homogeneous scale of 1.

```
Usage:     t = homotrans(P, v; checkinf = false)

Arguments:
          P  - 3 x 3 or 4 x 4 homogeneous transformation matrix
          v  - 3 x n or 4 x n matrix of homogeneous coordinates or ...
               2 x n or 3 x n matrix of inhomogeneous coordinates
Keyword Argument:
    checkinf - If true code will check if the homogeneous coordinates
               of any transformed point is at infinity (scale parameter
               is zero). If so, no normalisation of the point is attempted.

Returns   t  - Transformed coordinates. Homogeneous or inhomogeneous 
               to match input data v.
```

The input v is assumed inhomogeneous if the number of rows is equal to size(P,2) - 1
