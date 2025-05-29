```
ephem_spk_timespan(eph::EphemerisProvider)
```

Return the minimum and maximum time available in the SPK kernels loaded within `eph`, in  TDB seconds since J2000, together with a continuity parameter defined as follows: 

  * **0** no SPK data is available.
  * **1** the quantities of all bodies are available for any time between the first and last time.
  * **2** the quantities of some bodies are available on discontinuous time intervals between the    first and last time.
  * **3** the quantities of each body are available on a continuous time interval between the first    and the last time, but not available for any time between the first and last time.

### References

  * [CALCEPH](https://www.imcce.fr/inpop/calceph) C++ library

### See Also

See also [`ephem_pck_timespan`](@ref).
