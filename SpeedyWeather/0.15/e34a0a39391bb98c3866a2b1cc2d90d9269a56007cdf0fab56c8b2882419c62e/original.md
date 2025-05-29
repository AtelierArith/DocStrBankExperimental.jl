Create a struct `Earth<:AbstractPlanet`, with the following physical/orbital characteristics. Note that `radius` is not part of it as this should be chosen in `SpectralGrid`. Keyword arguments are

  * `rotation::AbstractFloat`: angular frequency of Earth's rotation [rad/s]
  * `gravity::AbstractFloat`: gravitational acceleration [m/s^2]
  * `daily_cycle::Bool`: switch on/off daily cycle
  * `length_of_day::Dates.Second`: Seconds in a daily rotation
  * `seasonal_cycle::Bool`: switch on/off seasonal cycle
  * `length_of_year::Dates.Second`: Seconds in an orbit around the sun
  * `equinox::Dates.DateTime`: time of spring equinox (year irrelevant)
  * `axial_tilt::AbstractFloat`: angle [˚] rotation axis tilt wrt to orbit
  * `solar_constant::AbstractFloat`: Total solar irradiance at the distance of 1 AU [W/m²]
