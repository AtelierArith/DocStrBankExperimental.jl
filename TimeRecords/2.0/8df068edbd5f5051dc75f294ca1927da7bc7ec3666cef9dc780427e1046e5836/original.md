findinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Base.RefValue{<:Integer})

Finds the indices of the time series (ts) where Δt[begin] <= ts.t <= Δt[end])  Stores the last value of hte index range for future use
