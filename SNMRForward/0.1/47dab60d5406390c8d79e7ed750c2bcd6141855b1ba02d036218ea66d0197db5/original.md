```
MRSForward(R::Real, zgrid::AbstractVector{<:Real},
qgrid::AbstractVector{<:Real}, ϕ::Real, Be::Real,
condLEM::ConductivityModel; nrvals = 200, temp=300.0,
qwe=true)
```

Returns an `MRSForward` forward modelling object, with the kernel computed for a circular loop.

Parameters:

  * `R`: loop radius in metres
  * `zgrid`: depth cell boundaries, in metres below surface.
  * `qgrid`: pulse moments used for the experiment, in Ampere-seconds.
  * `ϕ`: magnetic field inclination in radians.
  * `Be`: Earth field magnitude in Tesla.
  * `condLEM`: layered-earth conductivity model, as a `ConductivityModel` object.

Optional parameters:

  * `nrvals`: number of radial points to use to evaluate the horizontal integration of the kernel.
  * `temp`: temperature in Kelvin, affects the magnitude of equilibrium magnetisation.
  * `qwe`: whether to use quadrature with extrapolation (QWE) to evaluate Hankel transforms for the kernel.

This is slower, but more accurate at shallower depths, than the alternative 801-point digital filter.
