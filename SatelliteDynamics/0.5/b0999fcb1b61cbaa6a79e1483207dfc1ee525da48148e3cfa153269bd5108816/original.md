F10.7 cm solar flux data on the day in question.

Arguments:

  * `mjd::Real` Modified Julian date of desired data. Time system of input is UT1
  * `epc::Epoch` Epoch of desired input Time system of input is UT1

Returns:

  * `data::Tuple{Float64, Float64, Float64, Float64}` Flux data on the day in question

Elements are observed, adjusted, 81-observed average, 81-adjusted average.
