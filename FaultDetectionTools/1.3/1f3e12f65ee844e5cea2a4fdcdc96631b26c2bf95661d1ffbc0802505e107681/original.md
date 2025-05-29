```
S = fditspec_(sysrf::DescriptorStateSpace; FDfreq = missing, block = false, poleshift = false, 
             FDtol, FDStol, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

Compute the weak or strong binary structure matrix `S` of the transfer function matrix of a  linear time-invariant system `sysrf`  (typically representing the transfer channel from the fault inputs to residuals). `sysrf` has a descriptor system realization of the form `sysrf = (Af-lambda*Ef,Bf,Cf,Df)`  with a  `q x mf` transfer function matrix `Rf(λ)`.  For the description of keyword parameters see the documentation of [`fditspec`](@ref). 
