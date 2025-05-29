hnormalise! - In-place normalisation of homogeneous coordinates to a scale of 1

```
Usage:   hnormalise!(x)

Argument:
        x - An Nxnpts array of homogeneous coordinates.

Return value and side effect:
        x - The homogeneous coordinates in x are rescaled so
            that the scale values x[end,:] are all 1.
```

Note that any homogeneous coordinates at infinity (having a scale value of

0. are left unchanged.

See also: hnormalise()
