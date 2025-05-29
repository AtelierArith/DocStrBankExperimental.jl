```
offsetpoly(plist;
    startoffset = 10,
    endoffset   = 10,
    easingfunction = lineartween)
```

Return a closed polygon that is offset from and encloses an open polygon.

The incoming set of points `plist` is treated as an open polygon, and another set of points is created, which form a polygon lying `...offset` units away from the source poly.

This method for `offsetpoly()` treats the list of points as `n` vertices connected with `n - 1` lines. It allows you to vary the offset from the start of the line to the end.

The other method `offsetpoly(plist, d)` treats the list of points as `n` vertices connected with `n` lines.

# Extended help

This function accepts a keyword argument that allows you to control the offset using a function, using the easing functionality built in to Luxor. By default the function is `lineartween()`, so the offset changes linearly between the `startoffset` and the `endoffset`. The function:

```julia
f(a, b, c, d) = 2sin((a * π))
```

runs from 0 to 2 and back as `a` runs from 0 to 1. The offsets are scaled by this amount.
