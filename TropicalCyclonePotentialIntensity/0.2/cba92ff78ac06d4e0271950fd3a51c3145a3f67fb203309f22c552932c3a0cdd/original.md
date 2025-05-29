```
get_buoyancy_of_lifted_parcel(tparcel <: Real,rparcel <: Real,pparcel <: Real,t :: Array{<: Real},r :: Array{<: Real},p  :: Array{<: Real},ptop=50)
```

Get the buoyancy profile defined for each level `z` as the difference between the temperature of a parcel lifted from the level `p = pparcel` to the level `p(z)`.     `Buoyancy(z) = Tv_lifted(z) - Tv_env(z)` 

This computes the lifting condensation level (LCL) to decide if the parcel should be lifted adiabatically or not. If not adiabatically, it uses the Newton-Raphson method to find the temperature at a level while conserving specific entropy.     `Buoyancy(z) = Tv_lifted(z) - Tv_env(z)` 
