```
classification([T], p::PointRecord)
classification([T], points, inds = :)
```

Obtain the class that has been assigned to the point data record, as a UInt8 or the integer type `T`, if specified. Values in the range 0–63 either correspond to an ASPRS standard point class or are reserved for future standardization, whereas the meaning of values in the range 64–255 is user definable.

The ASPRS standard point classes are created/never classified (0), unclassified (1), ground (2), low vegetation (3), medium vegetation (4), high vegetation (5), building (6), low point/noise (7), water (9), rail (10), road surface (11), wire-guard/shield (13), wire-conductor/phase (14), transmission tower (15), wire-structure connector (16), bridge deck (17), high noise (18), overhead structure (19), ignored ground (20), snow (21), and temporal exclusion (22).

See also: [`PointRecord`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref), [`is_synthetic`](@ref), [`is_withheld`](@ref)
