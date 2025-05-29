Set Earth orientation data values for a specific date in the module global EarthOrientationData object.

Arguments:

  * `mjd::Real` Modified Julian Date in UTC of the Epoch for which the Earth orientation data is aligned to.
  * `ut1_utc::Real` Offset between UT1 and UTC in seconds.
  * `xp::Real` x-component of the pole locator in radians.
  * `yp::Real` y-component of the pole locator in radians.
