makeinhomogeneous - Converts homogeneous coords to inhomogeneous coordinates

```
Usage:  x = makehomogeneous(hx)

Argument:
        hx  - an N x npts array of homogeneous coordinates.

Returns:
        x - an (N-1) x npts array of inhomogeneous coordinates
```

Warning:  If there are any points at infinity (scale = 0) the coordinates of these points are simply returned minus their scale coordinate.

See also: makehomogeneous(), hnormalise()
