```
sphdist(long1, lat1, long2, lat2[, degrees=true]) -> angular_distance
```

### Purpose

Angular distance between points on a sphere.

### Arguments

  * `long1`:  longitude of point 1
  * `lat1`: latitude of point 1
  * `long2`: longitude of point 2
  * `lat2`: latitude of point 2
  * `degrees` (optional boolean keyword): if `true`, all angles, including the output distance, are assumed to be in degrees, otherwise they are all in radians.  It defaults to `false`.

### Output

Angular distance on a sphere between points 1 and 2, as an `AbstractFloat`.  It is expressed in radians unless `degrees` keyword is set to `true`.

### Example

```jldoctest
julia> using AstroLib

julia> sphdist(120, -43, 175, +22)
1.5904422616007134
```

### Notes

  * `gcirc` function is similar to `sphdist`, but may be more suitable for astronomical applications.

Code of this function is based on IDL Astronomy User's Library.
