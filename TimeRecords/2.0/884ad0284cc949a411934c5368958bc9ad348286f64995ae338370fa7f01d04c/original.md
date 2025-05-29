```
interpolate(f_extrap::Function, ts::AbstractTimeSeries, vt::AbstractVector{<:Real}; indhint=nothing)
```

Interpolates a TimeSeries ts::AbstractTimeSeries at timestamps vt::AbstractVector{<:Real} using a two-point algorithm Current two-point algorithms that are supported are zero-order-hold, first-order-interpolation
