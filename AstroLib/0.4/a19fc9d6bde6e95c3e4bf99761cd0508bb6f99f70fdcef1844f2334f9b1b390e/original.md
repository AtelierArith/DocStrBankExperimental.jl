```
tics(radec_min, radec_max, numx, ticsize[, ra=true]) -> ticsize, incr
```

### Purpose

Compute a nice increment between tic marks for astronomical images.

### Explanation

For use in labelling a displayed image with right ascension or declination axes.  An approximate distance between tic marks is input, and a new value is computed such that the distance between tic marks is in simple increments of the tic label values.

### Arguements

  * `radec_min` : minimum axis value (degrees).
  * `radec_min` : maximum axis value (degrees).
  * `numx` : number of pixels in x direction.
  * `ticsize` : distance between tic marks (pixels).
  * `ra` (optional boolean keyword): if true, incremental value would be in minutes of time. Default is false.

### Output

A 2-tuple `(ticsize, incr)`:

  * `ticsize` : distance between tic marks (pixels).
  * `incr` : incremental value for tic labels.  The format is dependent on the optional keyword. If true (i.e for right ascension), it's in minutes of time, else it's in minutes of arc (for declination).

### Example

```jldoctest
julia> using AstroLib

julia> tics(55, 60, 100.0, 1/2)
(0.66, 2.0)

julia> tics(30, 60, 12, 2, true)
(2.75, 30.0)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
