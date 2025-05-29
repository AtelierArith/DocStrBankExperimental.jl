```
check_cocos(B0, Ip, F::AbstractVector, pprime::AbstractVector, q::AbstractVector, psi::AbstracVector, cc::COCOS; verbose = false) -> Bool
```

Returns if equilibrium quantities are consistent with given COCOS

Arguments:

  * B0 - Toroidal magnetic field
  * Ip - Plasma current
  * F::AbstractVector - Poloidal current as a function of psi
  * pprime::AbstracVector - Pressure gradient w.r.t. psi as a function of psi
  * psi::AbstractVector - Poloidal flux
  * cc::Union{Int,COCOS} - COCOS structure or ID
