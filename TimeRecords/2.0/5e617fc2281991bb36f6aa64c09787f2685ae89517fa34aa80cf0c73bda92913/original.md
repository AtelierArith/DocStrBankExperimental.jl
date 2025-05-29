aggregate(f::Function, ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Union{Real,DateTime}}; order=0) where T <: Number

Aggregate a timeseries `ts` over intervals of `vt` using the aggregation function `f` with the following order options:      (order=0) which uses the Riemann integral     (order=1) which uses a trapezoidal integral
