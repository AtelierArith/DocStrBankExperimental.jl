```
premat(equinox1, equinox2[, FK4=true]) -> precession_matrix
```

### Purpose

Return the precession matrix needed to go from `equinox1` to `equinox2`.

### Explanation

This matrix is used by `precess` and `baryvel` to precess astronomical coordinates.

### Arguments

  * `equinox1`: original equinox of coordinates.
  * `equinox2`: equinox of precessed coordinates.
  * `FK4` (optional boolean keyword): if this keyword is set to `true`, the FK4 (B1950.0) system precession angles are used to compute the precession matrix. When it is `false`, the default, use FK5 (J2000.0) precession angles.

### Output

A 3×3 matrix, used to precess equatorial rectangular coordinates.

### Example

Return the precession matrix from 1950.0 to 1975.0 in the FK4 system

```jldoctest
julia> using AstroLib

julia> premat(1950, 1975, FK4=true)
3×3 StaticArraysCore.SMatrix{3, 3, Float64, 9} with indices SOneTo(3)×SOneTo(3):
 0.999981    -0.00558775  -0.00242909
 0.00558775   0.999984    -6.78691e-6
 0.00242909  -6.78633e-6   0.999997
```

### Method

FK4 constants from "Computational Spherical Astronomy" by Taff (1983), p. 24. (FK4). FK5 constants from "Explanatory Supplement To The Astronomical Almanac" 1992, page 104 Table 3.211.1 (https://archive.org/details/131123ExplanatorySupplementAstronomicalAlmanac).

### Notes

Code of this function is based on IDL Astronomy User's Library.
