```
r_mod_to_mj2000_iau2006([T, ]jd_tt::Number) -> T
```

Compute the rotation that aligns the Mean of Date (MOD) reference frame with the J2000 mean equatorial frame at Julian day `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-2006 theory.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the MOD frame with the MJ2000 frame.

# Remarks

The J2000 reference frame here is not equal to the previous definition in FK5 theory. It is the reason why it is internally called `MJ2000`. According to **[1]**:

> The mean equinox of J2000.0 to be considered is not the “rotational dynamical mean equinox of J2000.0” as used in the past, but the “inertial dynamical mean equinox of J2000.0” to which the recent numerical or analytical solutions refer.  The latter is associated with the ecliptic in the inertial sense, which is the plane perpendicular to the angular momentum vector of the orbital motion of the Earth-Moon barycenter as computed from the velocity of the barycenter relative to an inertial system. The rotational equinox is associated with the ecliptic in the rotational sense, which is perpendicular to the angular momentum vector computed from the velocity referred to the rotating orbital plane of the Earth-Moon barycenter. (The difference between the two angular momenta is the angular momentum associated with the rotation of the orbital plane.)


# References

  * **[1]**: IERS (2010). Transformation between the International Terrestrial Reference   System and the Geocentric Celestial Reference System. IERS Technical Note No. 36,   Chapter 5.
