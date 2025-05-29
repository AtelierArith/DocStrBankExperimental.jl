```
ephem_rotation12(eph::EphemerisProvider, from::Int, to::Int, time::Number)
```

Compute the 12-elements orientation angles of one set of axes (to) relative  to another (from) at `time`, expressed in TDB/TCB seconds since J2000, in accordance  with the kernel timescale.

!!! note
    For the orientation angles, it is not possible to automatically compute the  reverse transformation , i.e., if the orientation of PA440 is defined  with respect to the ICRF, it is not possible to compute the rotation from the  PA440 to the ICRF with this routine.

