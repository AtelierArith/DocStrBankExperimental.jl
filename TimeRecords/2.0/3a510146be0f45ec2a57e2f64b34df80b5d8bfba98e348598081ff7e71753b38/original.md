accumulate(ts::AbstractTimeSeries{T}; order=0) where T <: Number

Accumulate a timeseries over its time intervals, with the following order options:      (order=0) which uses the Riemann integral     (order=1) which uses a trapezoidal integral
