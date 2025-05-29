```
rattle!(sys, r::Union{AbstractFloat, Quantity}) -> at
```

Randomly perturbs the atom positions within a ball of radius `r`. The perturbation  is uniform in angular component, and uniform in radial component. (Note this is  not the same as choosing them uniform in cartesian coordinates!). 

If `r` is unitless, then the unit of the system is applied. 
