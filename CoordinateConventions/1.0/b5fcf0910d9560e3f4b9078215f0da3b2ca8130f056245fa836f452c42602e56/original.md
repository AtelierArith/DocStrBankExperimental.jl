```
identify_cocos(B0, Ip, q, psi, clockwise_phi, a)
```

Utility function to identify COCOS coordinate system. If multiple COCOS are possible, then all are returned.

Arguments:

  * B0 - toroidal magnetic field (with sign)
  * Ip - plasma current (with sign)
  * q  -  safety factor profile (with sign) as function of psi
  * psi::AbstractVector -  Vector of poloidal fluxs from the magnetic axis to the plasma boundary
  * clockwise_phi::Bool - (optional) [true, false] if phi angle is defined clockwise or not. This is required to identify odd Vs even COCOS. Note that this cannot be determined from the output of a code.
  * a::AbstractVector - (optional) flux surfaces minor radius as function of psi. This is required to identify 2*pi term in psi definition
