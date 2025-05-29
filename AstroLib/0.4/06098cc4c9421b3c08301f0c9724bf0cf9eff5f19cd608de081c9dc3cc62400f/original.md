```
true_obliquity(jd) -> t_eps
```

### Purpose

Return the true obliquity of the ecliptic for a given Julian date

### Explanation

The function is used by the [`co_aberration`](@ref) procedure.

### Arguments

  * `jd`: Julian date.

### Output

  * `t_eps`: true obliquity of the ecliptic, in radians

### Example

```jldoctest
julia> using AstroLib

julia> true_obliquity(jdcnv(1978,01,7,11, 01))
0.4090953896211926
```

### Notes

The function calls [`mean_obliquity`](@ref).
