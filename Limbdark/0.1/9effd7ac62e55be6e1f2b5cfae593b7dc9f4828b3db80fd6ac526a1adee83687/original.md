```
transit_poly(r,b,u_n)
```

Given a radius-ratio, impact parameter, vector of limb-darkening coefficients of size N, returns the flux (normalized to one for unocculted star) for a limb-darkened transit.

# Arguments

  * `r::Real`: The radius of the occultor in units of the radius of the occulted body.
  * `b::Real`: The (initial) impact parameter of the occultation.
  * `u_n::Array{Real,1}`: The array of limb darkening coefficients.  Size N.
