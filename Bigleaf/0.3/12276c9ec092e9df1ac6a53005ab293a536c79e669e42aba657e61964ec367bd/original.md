```
VPD_to_rH(VPD,Tair; ...)
H_to_VPD(rH,Tair; ...)
e_to_rH(e,Tair; ...)
VPD_to_e(VPD,Tair; ...)
e_to_VPD(e,Tair; ...)
e_to_q(e,pressure; ...)
q_to_e(q,pressure; ...)
q_to_VPD(q,Tair,pressure; ...)
VPD_to_q(VPD,Tair,pressure; ...)
```

Conversion between vapor pressure (e), vapor pressure deficit (VPD),              specific humidity (q), and relative humidity (rH).

# Arguments

  * Tair:      Air temperature (deg C)
  * pressure:  Atmospheric pressure (kPa)
  * e:         Vapor pressure (kPa)
  * q:        Specific humidity (kg kg-1)
  * VPD:       Vapor pressure deficit (kPa)
  * rH:        Relative humidity (-)

All functions accept the optional arguments:

  * `Esat_formula`: formula used in [`Esat_from_Tair`](@ref)
  * `constants`: dictionary from [`BigleafConstants`](@ref) with entries eps and Pa2kPa

# Rreferences

Foken, T, 2008: Micrometeorology_ Springer, Berlin, Germany.
