Compute the location of the pole. Returns x- and y- components as a tuple with the units of [radians].  If the EarthOrientationData argument is ommitted the function will use the default module-global value.

Arguments:

  * `eop::EarthOrientationData` EarthOrientationData object to use to compute the offset
  * `mjd::Real` Modified Julian Date in UTC of the Epoch for which the pole locator is desired.
  * `interp::Bool` Whether to linearly interpolate the parameter data to the input MJD.

Returns:

  * `pole_locator::Tuple{Float, Float}` (x, y) pole location in radians.
