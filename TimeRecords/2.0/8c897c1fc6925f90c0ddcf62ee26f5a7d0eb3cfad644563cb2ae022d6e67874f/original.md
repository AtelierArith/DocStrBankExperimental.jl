findbounds(ts::AbstractTimeSeries, t::Real, indhint::Integer)

Finds the index of the TimeRecord before and after t::Real; indhint is the first index searched for If t is not inside the timeseries, one of the bounds will not be in its index range If in-range bounds are desired, use clampedbounds(ts, t, indhint) instead
