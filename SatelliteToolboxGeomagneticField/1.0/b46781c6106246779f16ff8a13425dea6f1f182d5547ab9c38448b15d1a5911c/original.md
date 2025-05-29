```
geomagnetic_dipole_field(r_e::AbstractVector{T}, year::Number = 2020) where T -> SVector{3, T}
```

Compute the geomagnetic field [nT] using the simplified dipole model at position `r_e` (ECEF reference frame) [m]. This function uses the year `year` to obtain the position of the South geomagnetic pole (which lies in the North hemisphere) and the dipole moment. If `year` is omitted, it defaults to 2020.

# Remarks

1. The output vector will be represented in the ECEF reference frame.
2. The returned vector type is obtained by converting `T` to a float.
3. The south geomagnetic pole position and dipole moment is obtained by interpolating the  values provided in **[1]**.

# References

  * **[1]**: http://wdc.kugi.kyoto-u.ac.jp/poles/polesexp.html
