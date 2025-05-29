clampedbounds(ts::AbstractTimeSeries, t::Real, indhint=nothing)

Behaves like findbounds except that it always returns integer boundaries within the timeseries bounds Out-of-bound results yield repeating lower bounds, or repeating upper bounds
