getinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Integer=firstindex(ts))

タイムシリーズ (ts) の要素を返します (Δt[begin] <= ts.t <= Δt[end])
