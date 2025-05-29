Compute x-component of the Celestial Intermediate Pole offset (`dX`) in [radians]. If the first EarthOrientationData argument is ommitted the function will use the default module-global value.

Arguments:

  * `eop::EarthOrientationData` EarthOrientationData object to use to compute the offset
  * `mjd::Real` Modified Julian Date in UTC of the Epoch for which the `dX` value is desired.
  * `interp::Bool` Whether to linearly interpolate the parameter data to the input MJD.

Returns:

  * `dX::Float` x-component of pole offset in radians.
