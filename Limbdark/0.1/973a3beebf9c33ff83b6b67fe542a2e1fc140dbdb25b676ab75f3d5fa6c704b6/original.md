```
transit_poly!(r,b,u_n,dfdrbu)
```

Given a radius-ratio, impact parameter, vector of limb-darkening coefficients of size N, and pre-allocated vector for derivatives of size N+2, returns the flux (normalized to one for unocculted star) for a limb-darkened transit light curve and its gradient with respect to the input parameters is returned.

# Arguments

  * `r::Real`: The radius of the occultor in units of the radius of the occulted body.
  * `b::Real`: The (initial) impact parameter of the occultation.
  * `u_n::Array{Real,1}`: The array of limb darkening coefficients.  Size N.
  * `dfdrbu::Array{Real,1}`: Gradient of the flux with respect to all input parameters. Size is N+2
