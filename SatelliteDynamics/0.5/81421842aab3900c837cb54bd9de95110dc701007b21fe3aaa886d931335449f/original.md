Compute the number of elapsed seconds since a given Epoch from the day number. Can be used to compute the elapsed time since a given Julian or Modified Julian Date.

Arguments:

  * `day_number::Real`: Day number, can contain fractional days. Asummes all days are a uniform 86400.0 seconds in length.
  * `day_epoch::Real`: Modified Julian Date of Epoch

Returns:

  * `t::Float`: Number of elapsed seconds between the Provided Modified   Julian date and the epoch.
