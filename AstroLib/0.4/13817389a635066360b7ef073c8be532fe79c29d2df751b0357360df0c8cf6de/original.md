```
precess_xyz(x, y, z, equinox1, equinox2) -> prec_x, prec_y, prec_z
```

### Purpose

Precess equatorial geocentric rectangular coordinates.

### Arguments

  * `x`, `y`, `z`: scalars or vectors giving heliocentric rectangular coordinates.
  * `equinox1`: original equinox of coordinates, numeric scalar.
  * `equinox2`: equinox of precessed coordinates, numeric scalar.

Input coordinates can be given also a 3-tuple `(x, y, z)`.

### Output

The 3-tuple `(x, y, z)` of coordinates modified by precession.

### Example

Precess 2000 equinox coordinates `(1, 1, 1)` to 2050.

```jldoctest
julia> using AstroLib

julia> precess_xyz(1, 1, 1, 2000, 2050)
(0.9838854500981734, 1.0110925876508692, 1.0048189888146941)
```

### Method

The equatorial geocentric rectangular coordinates are converted to right ascension and declination, precessed in the normal way, then changed back to `x`, `y` and `z` using unit vectors.

### Notes

Code of this function is based on IDL Astronomy User's Library.
