Compute the offset between the UT1 and UTC time systems in seconds. If the EarthOrientationData argument is ommitted the function will use the default module-global value.

Arguments:

  * `eop::EarthOrientationData` EarthOrientationData object to use to compute the offset
  * `mjd::Real` Modified Julian Date in UTC of the Epoch for which the UT1-UTC offset is desired.
  * `interp::Bool` Whether to linearly interpolate the parameter data to the input MJD.

Returns:

  * `ut1_utc::Float` UT1 - UTC offset. [s]
