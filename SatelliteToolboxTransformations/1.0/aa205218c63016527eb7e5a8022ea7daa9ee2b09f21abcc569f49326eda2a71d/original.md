```
ecef_to_ned(r_ecef::AbstractVector{T1}, lat::T2, lon::T3, h::T4; translate::Bool = false) -> SVector{3, T}
```

Convert a vector `r_ecef` represented in the Earth-Centered, Earth-Fixed (ECEF) frame to the local reference frame NED (North, East, Down) at the geodetic position `lat` [rad], `lon` [rad], and `h` [m].

If `translate` is `false`, this function computes only the rotation between ECEF and NED. Otherwise, it will also translate the vector considering the distance between the Earth's center and NED origin.

The element type `T` of the returned vector is obtained by promoting `T1`, `T2`, `T3`, and `T4` to a float.

# Remarks

This algorithm was based on the information in **[1]**.

# References

  * **[1]**: [Transformations between ECEF and ENU   coordinates](https://gssc.esa.int/navipedia/index.php/Transformations_between_ECEF_and_ENU_coordinates)
