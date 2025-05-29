```
ned_to_ecef(r_ned::AbstractVector{T1}, lat::T2, lon::T3, h::T4; translate::Bool = false) -> SVector{3, T}
```

Convert a vector `r_ned` represented in the local reference frame NED (North, East, Down) at the geodetic position `lat` [rad], `lon` [rad], and `h` [m] to the Earth-Centered, Earth-Fixed (ECEF) frame.

If `translate` is `false`, then this function computes only the rotation between NED and ECEF. Otherwise, it will also translate the vector considering the distance between the Earth's center and NED origin.

The element type `T` of the returned vector is obtained by promoting `T1`, `T2`, `T3`, and `T4` to a float.

# Remarks

This algorithm was based on the information in **[1]**.

# References

  * **[1]** [Transformations between ECEF and ENU   coordinates](https://gssc.esa.int/navipedia/index.php/Transformations_between_ECEF_and_ENU_coordinates)
