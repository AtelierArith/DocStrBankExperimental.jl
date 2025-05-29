```
compute(eph,jd0,time,target,center)
```

Compute position and velocity of target with respect to center at epoch jd0+time. This method does not support the NAIF numbering scheme. To get the best precision for the interpolation, the time is split in two floating-point numbers. The argument jd0 should be an integer and time should be a fraction of the day. But you may call this function with time=0 and jd0, the desired time, if you don't care about precision.

This method does not support the NAIF body identification scheme.

Output units are:

  * AU and AU/day for position and velocity
  * rad and rad/day for librations
  * second and unitless for time ephemeris and time ephemeris rate

# Arguments

  * `eph`: ephemeris
  * `jd0::Float64`: jd0+time must be equal to the Julian Day for the time coordinate corresponding to the ephemeris (usually TDB or TCB)
  * `time::Float64`: jd0+time must be equal to the Julian Day for the time coordinate corresponding to the ephemeris (usually TDB or TCB)
  * `target::Integer`: The body or reference point whose coordinates are required.
  * `center::Integer`: The origin of the coordinate system.

The possible values for target and center are :

  * 1 : Mercury Barycenter
  * 2 : Venus Barycenter
  * 3 : Earth
  * 4 : Mars Barycenter
  * 5 : Jupiter Barycenter
  * 6 : Saturn Barycenter
  * 7 : Uranus Barycenter
  * 8 : Neptune Barycenter
  * 9 : Pluto Barycenter
  * 10    : Moon
  * 11    : Sun
  * 12    : Solar Sytem barycenter
  * 13    : Earth-moon barycenter
  * 14    : Nutation angles
  * 15    : Librations
  * 16    : TT-TDB
  * 17    : TCG-TCB
  * asteroid number + 2000000    : asteroid
