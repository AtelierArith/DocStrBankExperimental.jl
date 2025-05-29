```
check_cocos(sigma_B0, sigma_Ip, sigma_F, sigma_pprime, sigma_q, sigma_dpsi, cc::COCOS; verbose = false) -> Bool
```

Returns if equilibrium quantities are consistent with given COCOS

Arguments:

  * sigma_B0 - Toroidal magnetic field sign
  * sigma_Ip - Plasma current sign
  * sigma_F - Poloidal current sign
  * sigma_pprime - Pressure gradient sign
  * sigma_dpsi - dpsi/dr sign
  * cc::Union{Int,COCOS} - COCOS structure or ID
