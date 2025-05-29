```
aitoff(l, b) -> x, y
```

### Purpose

Convert longitude `l` and latitude `b` to `(x, y)` using an Aitoff projection.

### Explanation

This function can be used to create an all-sky map in Galactic coordinates with an equal-area Aitoff projection.  Output map coordinates are zero longitude centered.

### Arguments

  * `l`: longitude, scalar or vector, in degrees.
  * `b`: latitude, number of elements as `l`, in degrees.

Coordinates can be given also as a 2-tuple `(l, b)`.

### Output

2-tuple `(x, y)`.

  * `x`: x coordinate, same number of elements as `l`.  `x` is normalized to be in $[-180, 180]$.
  * `y`: y coordinate, same number of elements as `l`.  `y` is normalized to be in $[-90, 90]$.

### Example

Get $(x ,y)$ Aitoff coordinates of Sirius, whose Galactic coordinates are $(227.23, -8.890)$.

```jldoctest
julia> using AstroLib

julia> x, y = aitoff(227.23, -8.890)
(-137.92196683723276, -11.772527357473054)
```

### Notes

See [AIPS memo No. 46](http://www.aips.nrao.edu/TEXT/PUBL/AIPSMEMO46.PS), page 4, for details of the algorithm.  This version of `aitoff` assumes the projection is centered at `b=0` degrees.

Code of this function is based on IDL Astronomy User's Library.
