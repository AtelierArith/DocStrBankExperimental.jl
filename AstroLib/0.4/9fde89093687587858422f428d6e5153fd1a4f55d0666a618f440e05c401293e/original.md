```
eqpole(l, b[; southpole = false]) -> x, y
```

### Purpose

Convert right ascension $l$ and declination $b$ to coordinate $(x, y)$ using an equal-area polar projection.

### Explanation

The output $x$ and $y$ coordinates are scaled to be in the range $[-90, 90]$ and to go from equator to pole to equator.  Output map points can be centered on the north pole or south pole.

### Arguments

  * `l`: longitude, scalar or vector, in degrees
  * `b`: latitude, same number of elements as right ascension, in degrees
  * `southpole` (optional boolean keyword): keyword to indicate that the plot is to be centered on the south pole instead of the north pole.  Default is `false`.

### Output

The 2-tuple $(x, y)$:

  * $x$ coordinate, same number of elements as right ascension, normalized to be in the range $[-90, 90]$.
  * $y$ coordinate, same number of elements as declination, normalized to be in the range $[-90, 90]$.

### Example

```jldoctest
julia> using AstroLib

julia> eqpole(100, 35, southpole=true)
(-111.18287262822456, -19.604540237028665)

julia> eqpole(80, 19)
(72.78853915267848, 12.83458333897169)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
