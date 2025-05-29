findbounds(ts::AbstractTimeSeries, t::Real, indhint::Base.RefValue{<:Integer})

Finds the index of the TimeRecord before and after t::Real; indhint is the first index searched for Previous results are saved in indhint in order to provide hits for future calls if they're made in order If t is not inside the timeseries, one of the bounds will not be in its index range If in-range bounds are desired, use clampedbounds(ts, t, indhint) instead
