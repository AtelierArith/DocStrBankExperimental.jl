```
strictinterp(f_interp::Function, ts::AbstractTimeSeries, vt::AbstractVector{<:Real}; indhint=nothing)
```

Interpolates a TimeSeries ts::AbstractTimeSeries at timestamps vt::AbstractVector{<:Real} using a two-point interpolation algorithm f_interp If teh timestamp is not inside the timeseries interval, 'missing' is returned Current two-point algorithms that are supported are zero-order-hold, first-order-interpolation
