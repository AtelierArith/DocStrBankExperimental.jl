```
mean_obliquity(jd) -> m_eps
```

### Purpose

Return the mean obliquity of the ecliptic for a given Julian date

### Explanation

The function is used by the [`co_nutate`](@ref) procedure.

### Arguments

  * `jd`: julian date

### Output

  * `m_eps`: mean obliquity of the ecliptic, in radians

### Example

```jldoctest
julia> using AstroLib

julia> mean_obliquity(jdcnv(1978,01,7,11, 01))
0.4091425159336512
```

### Notes

The algorithm used to find the mean obliquity(`eps0`) is mentioned in USNO Circular 179, but the canonical reference for the IAU adoption is apparently Hilton et al., 2006, Celest.Mech.Dyn.Astron. 94, 351. 2000
