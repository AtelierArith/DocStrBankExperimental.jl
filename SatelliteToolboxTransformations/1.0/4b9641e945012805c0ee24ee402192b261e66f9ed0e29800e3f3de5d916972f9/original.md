```
r_itrf_to_pef_fk5([T, ]x_p::Number, y_p::Number) -> T
```

Compute the rotation that aligns the International Terrestrial Reference Frame (ITRF) with the Pseudo-Earth Fixed (PEF) frame considering the polar motion represented by the angles `x_p` [rad] and `y_p` [rad] that are obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

`x_p` is the polar motion displacement about X-axis, which is the IERS Reference Meridian direction (positive south along the 0˚ longitude meridian). `y_p` is the polar motion displacement about Y-axis (90˚W or 270˚E meridian).

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the ITRF frame with the PEF frame.

# Remarks

The ITRF is defined based on the International Reference Pole (IRP), which is the location of the terrestrial pole agreed by international committees **[1]**.  The Pseudo-Earth Fixed, on the other hand, is defined based on the Earth axis of rotation, or the Celestial Intermediate Pole (CIP). Hence, PEF XY-plane contains the True Equator. Furthermore, since the recovered latitude and longitude are sensitive to the CIP, then it should be computed considering the PEF frame.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
