```
radec(ra::Real, dec::Real[, hours=false]) -> ra_hours, ra_minutes, ra_seconds, dec_degrees, dec_minutes, dec_seconds
```

### Purpose

Convert right ascension and declination from decimal to sexagesimal units.

### Explanation

The conversion is to sexagesimal hours for right ascension, and sexagesimal degrees for declination.

### Arguments

  * `ra`: decimal right ascension, scalar or array.  It is expressed in degrees, unless the optional keyword `hours` is set to `true`.
  * `dec`: declination in decimal degrees, scalar or array, same number of elements as `ra`.
  * `hours` (optional boolean keyword): if `false` (the default), `ra` is assumed to be given in degrees, otherwise `ra` is assumed to be expressed in hours.

### Output

A 6-tuple of `AbstractFloat`:

```
(ra_hours, ra_minutes, ra_seconds, dec_degrees, dec_minutes, dec_seconds)
```

If `ra` and `dec` are arrays, also each element of the output 6-tuple are arrays of the same dimension.

### Example

Position of Sirius in the sky is (ra, dec) = (6.7525, -16.7161), with right ascension expressed in hours.  Its sexagesimal representation is given by

```jldoctest
julia> using AstroLib

julia> radec(6.7525, -16.7161, hours=true)
(6.0, 45.0, 9.0, -16.0, 42.0, 57.9600000000064)
```
