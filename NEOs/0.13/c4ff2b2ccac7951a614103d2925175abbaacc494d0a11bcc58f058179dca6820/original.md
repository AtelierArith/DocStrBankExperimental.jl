```
mtp(xae::Vector{U}) where {U <: Number}
```

Return the cartesian coordinates [Earth radii] on the modified target plane of an asteroid's close approach with the Earth.

# Arguments

  * `xae::Vector{U}`: asteroid's geocentric position/velocity  vector at close approach [au, au/day].

!!! reference
    See equations (43)-(44) in page 15 of https://doi.org/10.1007/s10569-019-9914-4.

