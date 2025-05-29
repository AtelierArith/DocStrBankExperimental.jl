```
 fdisspec_(sysrf::DescriptorStateSpace, freq; block = false, stabilize = false, FDGainTol = 0.01, 
                 atol, atol1, atol2, atol3, rtol, fast = true) -> (S, gains)
```

Compute the strong binary structure matrix `S` of the transfer function matrix of a  linear time-invariant system `sysrf`  (typically representing the transfer channel from the fault inputs to residuals). `sysrf` has a descriptor system realization of the form `sysrf = (Af-lambda*Ef,Bf,Cf,Df)`  with a  `q x mf` transfer function matrix `Rf(λ)`.  For the description of keyword parameters see the documentation of [`fdisspec`](@ref). 
