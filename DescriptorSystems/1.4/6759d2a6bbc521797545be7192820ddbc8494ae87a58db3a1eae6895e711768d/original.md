```
gnugap(sys1, sys2; freq = ω, rtolinf = 0.00001, fast = true, offset = sqrt(ϵ), 
       atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (nugapdist, fpeak)
```

Compute the ν-gap distance `nugapdist` between two descriptor systems `sys1 = (A1-λE1,B1,C1,D1)` and  `sys2 = (A2-λE2,B2,C2,D2)` and the corresponding frequency `fpeak` (in rad/TimeUnit), where the ν-gap  distance achieves its peak value. 

If `freq = missing`, the resulting `nugapdist` satisfies `0 <= nugapdist <= 1`.  The value `nugapdist = 1` results, if the winding number is different of zero in which case `fpeak = []`. 

If `freq = ω`, where `ω` is a given vector of real frequency values, the resulting `nugapdist` is a vector  of pointwise ν-gap distances of the dimension of `ω`, whose components satisfies `0 <= maximum(nugapdist) <= 1`.  In this case, `fpeak` is the frequency for which the pointwise distance achieves its peak value.  All components of `nugapdist` are set to 1 if the winding number is different of zero in which case `fpeak = []`.

The stability boundary offset, `β`, to be used to assess the finite zeros which belong to the boundary of the stability domain can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system, these are the finite zeros having  real parts within the interval `[-β,β]`, while for a discrete-time system,  these are the finite zeros having moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

Pencil reduction algorithms are employed to compute range and coimage spaces  which perform rank decisions based on rank  revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A1`, `A2`, `B1`, `B2`, `C1`, `C2`, `D1` and `D2`, the absolute tolerance for the nonzero elements of `E1` and `E2`,    and the relative tolerance for the nonzero elements of all above matrices.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the maximum of the orders of the systems `sys1` and `sys2`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The keyword argument `rtolinf` specifies the relative accuracy to be used  to compute the ν-gap as the infinity norm of the relevant system according to [1].  The default value used for `rtolinf` is `0.00001`.

*Method:* The evaluation of ν-gap uses the definition proposed in [1], extended to generalized LTI (descriptor) systems. The computation of winding number is based on enhancements covering zeros on the boundary of the  stability domain and infinite zeros.

*References:*

[1] G. Vinnicombe. Uncertainty and feedback: H∞ loop-shaping and the ν-gap metric.      Imperial College Press, London, 2001. 
