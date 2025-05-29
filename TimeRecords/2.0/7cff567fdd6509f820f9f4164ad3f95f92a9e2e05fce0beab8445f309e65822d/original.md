findbounds(ts::AbstractTimeSeries, t::Real)

Finds the index of the TimeRecord before and after t::Real using the bisection method If t is not inside the timeseries, one of the bounds will not be in its index range If in-range bounds are desired, use clampedbounds(ts, t, indhint) instead
