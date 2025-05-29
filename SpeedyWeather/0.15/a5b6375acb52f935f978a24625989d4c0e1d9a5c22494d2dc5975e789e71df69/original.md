Boundary layer drag coefficient from the bulk Richardson number, following Frierson, 2006, Journal of the Atmospheric Sciences.

  * `κ::Any`: von Kármán constant [1]
  * `z₀::Any`: roughness length [m]
  * `Ri_c::Any`: Critical Richardson number for stable mixing cutoff [1]
  * `drag_max::Base.RefValue`: Maximum drag coefficient, κ²/log(zₐ/z₀) for zₐ from reference temperature
