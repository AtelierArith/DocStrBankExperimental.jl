```
interpolate(ts::AbstractTimeSeries, t::Union{<:Real, AbstractVector{<:Real}}; order=0)
```

Interpolates timeseries ts::AbstractTimeSeries, at times vt::AbstractVector{Real} Returns a vector of values corresponding to timestamps vt Keyword "order" selects algorithm: Supports zero-order-hold (order=0) and first-order-interpolation (order=1)
