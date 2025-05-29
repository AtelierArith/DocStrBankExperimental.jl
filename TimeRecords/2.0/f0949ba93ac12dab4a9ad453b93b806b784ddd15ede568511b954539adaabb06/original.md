findinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Integer=firstindex(ts))

Finds the indices of the time series (ts) where Δt[begin] <= ts.t <= Δt[end]) 
