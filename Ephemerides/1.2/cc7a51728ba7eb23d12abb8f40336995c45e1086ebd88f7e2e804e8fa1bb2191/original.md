```
ephem_pck_timespan(eph::EphemerisProvider)
```

Return the minimum and maximum time available in the PCK kernels loaded within `eph`, in  TDB seconds since J2000, together with a continuity parameter defined as follows: 

  * **0** no PCK data is available.
  * **1** the quantities of all axes are available for any time between the first and last time.
  * **2** the quantities of some axes are available on discontinuous time intervals between the    first and last time.
  * **3** the quantities of each axis are available on a continuous time interval between the first    and the last time, but not available for any time between the first and last time.

### References

  * [CALCEPH](https://www.imcce.fr/inpop/calceph) C++ library

### See Also

See also [`ephem_spk_timespan`](@ref).
