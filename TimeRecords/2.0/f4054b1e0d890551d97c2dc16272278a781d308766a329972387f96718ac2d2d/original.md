getinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Integer=firstindex(ts))

Return the elements of the Timeseries (ts) where Δt[begin] <= ts.t <= Δt[end]) 
