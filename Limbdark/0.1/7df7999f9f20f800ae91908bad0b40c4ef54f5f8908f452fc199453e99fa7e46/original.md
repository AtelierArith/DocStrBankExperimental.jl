```
transit_init(r,b,u_n,grad)
```

Initialize and return a transit structure. This structure holds user-facing information about the transit as well as internal temporary variables used for computing the light curve. Pass an instance of this structure to `transit_poly()` to compute the actual flux.

# Arguments

  * `r::Real`: The radius of the occultor in units of the radius of the occulted body.
  * `b::Real`: The (initial) impact parameter of the occultation.
  * `u_n::Array{Real,1}`: The array of limb darkening coefficients.
  * `grad::Bool`: Compute the gradient of the flux as well?
