```
identify_cocos(sigma_B0, sigma_Ip, sigma_q, sigma_dpsi, clockwise_phi) -> List of possible COCOS IDs
```

Utility function to identify COCOS coordinate system. If multiple COCOS are possible, then all are returned.

Arguments:

  * sigma_B0 - (+1,-1) sign of the toroidal magnetic field
  * sigma_Ip - (+1,-1) sign of toroidal plasma current
  * sigma_q  - (+1,-1) sign of the safety factor (q) within the plasma
  * sigma_dpsi -  +1 if psi is increasing, -1 if psi is decreasing
  * clockwise_phi::Bool - (optional) [true, false] if phi angle is defined clockwise or not. This is required to identify odd Vs even COCOS. Note that this cannot be determined from the output of a code.
