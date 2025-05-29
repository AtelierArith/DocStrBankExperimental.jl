hnormalise - Normalises array of homogeneous coordinates to a scale of 1

```
Usage:  nx = hnormalise(x)

Argument:
        x  - an Nxnpts array of homogeneous coordinates.

Returns:
        nx - an Nxnpts array of homogeneous coordinates rescaled so
             that the scale values nx[end,:] are all 1.
```

Note that any homogeneous coordinates at infinity (having a scale value of

0. are left unchanged.

See also: hnormalise!()
