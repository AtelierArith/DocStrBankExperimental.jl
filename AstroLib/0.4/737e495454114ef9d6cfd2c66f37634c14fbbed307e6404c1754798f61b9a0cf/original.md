```
ticpos(deglen, pixlen, ticsize) -> ticsize, incr, units
```

### Purpose

Specify distance between tic marks for astronomical coordinate overlays.

### Explanation

User inputs number an approximate distance between tic marks, and the axis length in degrees. `ticpos` will return a distance between tic marks such that the separation is a round multiple in arc seconds, arc minutes, or degrees.

### Arguments

  * `deglen`: length of axis in degrees, positive scalar
  * `pixlen`: length of axis in plotting units (pixels), postive scalar
  * `ticsize`: distance between tic marks (pixels).  This value will be  adjusted by `ticpos` such that the distance corresponds to a round  multiple in the astronomical coordinate.

### Output

The 3-tuple `(ticsize, incr, units)`:

  * `ticsize`: distance between tic marks (pixels), positive scalar
  * `incr`: incremental value for tic marks in round units given  by the `units` parameter
  * `units`: string giving units of ticsize, either 'Arc Seconds', 'Arc Minutes', or 'Degrees'

### Example

Suppose a 512 × 512 image array corresponds to 0.2 × 0.2 degrees on the sky. A tic mark is desired in round angular units, approximately every 75 pixels. Then

```jldoctest
julia> using AstroLib

julia> ticpos(0.2, 512, 75)
(85.33333333333333, 2.0, "Arc Minutes")
```

i.e. a good tic mark spacing is every 2 arc minutes, corresponding to 85.333 pixels.

### Notes

All the arguments taken as input are assumed to be positive in nature.

Code of this function is based on IDL Astronomy User's Library.
