```
recpol(x, y[, degrees=false]) -> radius, angle
```

### Purpose

Convert 2D rectangular coordinates to polar coordinates.

### Explanation

This is the partial inverse function of `polrec`.

### Arguments

  * `x`: the abscissa coordinate of the point.  It may be a scalar or an array.
  * `y`: the ordinate coordinate of the point.  It may be a scalar or an array of the same lenth as `x`.
  * `degrees` (optional boolean keyword): if `true`, the output `angle` is given in degrees, otherwise in radians.  It defaults to `false`.

Mandatory arguments may also be passed as the 2-tuple `(x, y)`, so that it is possible to execute `polrec(recpol(x, y))`.

### Output

A 2-tuple `(radius, angle)` with the polar coordinates of the input.  The coordinate `angle` coordinate lies in the range $[-π, π]$ if `degrees=false`, or $[-180, 180]$ when `degrees=true`.

If `x` and `y` are arrays, `radius` and `angle` are arrays of the same length as `radius` and `angle`.

### Example

Calculate polar coordinates $(r, φ)$ of point with rectangular coordinates $(x, y) = (2.24, -1.87)$.

```jldoctest
julia> using AstroLib

julia> r, phi = recpol(2.24, -1.87)
(2.9179616172938263, -0.6956158538564537)
```

Angle $φ$ is given in radians.
