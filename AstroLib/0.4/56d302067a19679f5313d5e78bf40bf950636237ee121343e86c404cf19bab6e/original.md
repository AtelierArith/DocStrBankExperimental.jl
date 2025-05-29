```
precess_cd(cd, epoch1, epoch2, crval_old, crval_new[, FK4=true]) -> cd
```

### Purpose

Precess the coordinate description matrix.

### Explanation

The coordinate matrix is precessed from epoch1 to epoch2.

### Arguments

  * `cd`: 2×2 coordinate description matrix in degrees
  * `epoch1`: original equinox of coordinates, scalar
  * `epoch2`: equinox of precessed coordinates, scalar
  * `crval_old`: 2 element vector containing right ascension and declination in degrees of the reference pixel in the original equinox
  * `crval_new`: 2 element vector giving crval in the new equinox
  * `FK4` (optional boolean keyword): if this keyword is set to `true`, then the precession constants are taken in the FK4 reference frame. When it is `false`, the default is the FK5 frame

### Output

  * `cd`: coordinate description containing precessed values

### Example

```jldoctest
julia> using AstroLib

julia> precess_cd([20 60; 45 45], 1950, 2000, [34, 58], [12, 83])
2×2 Matrix{Float64}:
  48.8944  147.075
 110.188   110.365
```

### Notes

Code of this function is based on IDL Astronomy User's Library. This function should not be used for values more than 2.5 centuries from the year 1900. This function calls [`sec2rad`](@ref), [`precess`](@ref) and [`bprecess`](@ref).
