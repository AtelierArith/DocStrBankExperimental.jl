findinner(ts::AbstractTimeSeries, Δt::TimeInterval, indhint::Integer=firstindex(ts))

時間系列 (ts) のインデックスを見つけます (Δt[begin] <= ts.t <= Δt[end]) となる場所。
