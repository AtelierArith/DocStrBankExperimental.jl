```
polrec(radius, angle[, degrees=true]) -> x, y
```

### Purpose

Convert 2D polar coordinates to rectangular coordinates.

### Explanation

This is the partial inverse function of `recpol`.

### Arguments

  * `radius`: radial coordinate of the point.  It may be a scalar or an array.
  * `angle`: the angular coordinate of the point.  It may be a scalar or an array of the same lenth as `radius`.
  * `degrees` (optional boolean keyword): if `true`, the `angle` is assumed to be in degrees, otherwise in radians.  It defaults to `false`.

Mandatory arguments can also be passed as the 2-tuple `(radius, angle)`, so that it is possible to execute `recpol(polrec(radius, angle))`.

### Output

A 2-tuple `(x, y)` with the rectangular coordinate of the input.  If `radius` and `angle` are arrays, `x` and `y` are arrays of the same length as `radius` and `angle`.

### Example

Get rectangular coordinates $(x, y)$ of the point with polar coordinates $(r, φ) = (1.7, 227)$, with angle $φ$ expressed in degrees.

```jldoctest
julia> using AstroLib

julia> x, y = polrec(1.7, 227, degrees=true)
(-1.1593972121062475, -1.2433012927525897)
```
