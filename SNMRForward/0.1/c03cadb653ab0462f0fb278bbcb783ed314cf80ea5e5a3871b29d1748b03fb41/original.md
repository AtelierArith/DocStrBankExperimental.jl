```
MRSForward_square(L::Real, zgrid::AbstractVector{<:Real},
qgrid::AbstractVector{<:Real}, ϕ::Real, θ::Real, Be::Real,
condLEM::ConductivityModel; nxpoints = 128, temp=300.0)
```

Returns an `MRSForward` forward modelling object, with the kernel computed for a square loop.

Parameters:

  * `L`: loop radius in metres
  * `zgrid`: depth cell boundaries, in metres below surface.
  * `qgrid`: pulse moments used for the experiment, in Ampere-seconds.
  * `ϕ`: magnetic field inclination in radians.
  * `θ`: horizontal angle between loop orientation and magnetic north, in radians.
  * `Be`: Earth field magnitude in Tesla.
  * `condLEM`: layered-earth conductivity model, as a `ConductivityModel` object.

Optional parameters:

  * `nxpoints`: number of points to use in each dimension for the horizontal integration of the kernel.
  * `temp`: temperature in Kelvin, affects the magnitude of equilibrium magnetisation.
