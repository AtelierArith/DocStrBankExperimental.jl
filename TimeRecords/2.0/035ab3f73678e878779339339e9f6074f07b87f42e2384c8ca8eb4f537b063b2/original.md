initialhint!(indhint::Base.RefValue, ts::AbstractTimeSeries, t::Real)

Initializes a RefValue with the last index of ts that is less than or equal to t (uses bisection method)
