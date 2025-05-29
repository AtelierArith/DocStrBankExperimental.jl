```
iau_1980_nutation(date)
```

IAU 1980 nutation angles

# Argument

  * `date::AbstractFloat`: date of nutation (in TT)

# Returns

  * `angles::Tuple{AbstractFloat}`: nutation angles ψ, ϵ (in radians)

The nutation angles are with respect to the ecliptic of date.
