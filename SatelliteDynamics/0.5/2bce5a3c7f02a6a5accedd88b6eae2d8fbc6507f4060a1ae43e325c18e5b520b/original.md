Computes the day number in a given time scale given the elapsed time since epoch and the epoch itself.

Assumes all days are counted using a uniform 86400.0 seconds over the time span.

Arguments:

  * `t::Real`: Elapsed seconds since the `day_epoch`.
  * `day_epoch::Real`: Day number of the epoch. Common values are `SatelliteDynamics.MJD_ZERO` (to get the Julian Day number) or `SatelliteDynamics.MJD2000` (to get Modified Julian Days if reckoning time from January 1, 2000 0H)

Returns:

  * `days::Float`: Number of elapsed days in the time scale.
