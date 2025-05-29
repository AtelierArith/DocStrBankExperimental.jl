```
 opnorm(sys[, p = Inf]; kwargs...) 
 opnorm(sys, 2; kwargs...) -> sysnorm
 opnorm(sys, Inf; kwargs...) -> (sysnorm, fpeak)
 opnorm(sys; kwargs...) -> (sysnorm, fpeak)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`,  the `L2` or `L∞` system norm `sysnorm` induced by the vector `p`-norm, where valid values of `p` are `2` or `Inf`.  For the `L∞` norm, the frequency `fpeak` is also returned, where `G(λ)` achieves its peak gain.  See [`gh2norm`](@ref) and [`ghinfnorm`](@ref) for a description of the allowed keyword arguments.  
