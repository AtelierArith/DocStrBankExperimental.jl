```
euler(ai, bi, select[, FK4=true, radians=true])
```

### Purpose

Transform between Galactic, celestial, and ecliptic coordinates.

### Explanation

The function is used by the astro procedure.

### Arguments

  * `ai`: input longitude, scalar or vector.
  * `bi`: input latitude, scalar or vector.
  * `select` : integer input specifying type of coordinate transformation. SELECT   From          To     | SELECT   From       To    1   RA-Dec (2000) Galactic |   4    Ecliptic   RA-Dec    2   Galactic      RA-DEC   |   5    Ecliptic   Galactic    3   RA-Dec        Ecliptic |   6    Galactic   Ecliptic
  * `FK4` (optional boolean keyword) : if this keyword is set to `true`, then input and output celestial and ecliptic coordinates should be given in equinox B1950. When `false`, by default, they should be given in equinox J2000.
  * `radians` (optional boolean keyword) : if this keyword is set to `true`, all input and output angles are in radians rather than degrees.

### Output

a 2-tuple `(ao, bo)`:

  * `ao`: output longitude in degrees.
  * `bo`: output latitude in degrees.

### Example

Find the Galactic coordinates of Cyg X-1 (ra=299.590315, dec=35.201604)

```jldoctest
julia> using AstroLib

julia> euler(299.590315, 35.201604, 1)
(71.33498957116959, 3.0668335310640984)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
