Compute the y-component of the pole locator in [radians]. If the first EarthOrientationData argument is ommitted the function will use the default module-global value.

Arguments:

  * `eop::EarthOrientationData` EarthOrientationData object to use to compute the offset
  * `mjd::Real` Modified Julian Date in UTC of the Epoch for which the yp value is desired.
  * `interp::Bool` Whether to linearly interpolate the parameter data to the input MJD.

Returns:

  * `yp::Float` y-component of pole locator in radians.
