```
strictinterp(ts::AbstractTimeSeries, t::Union{<:Real, AbstractVector{<:Real}}; order=0)
```

Interpolates timeseries ts::AbstractTimeSeries, at times vt::AbstractVector{Real} If timestamp t is not bounded by the series, `missing` is returned Returns a vector of values corresponding to timestamps vt Keyword "order" selects algorithm: Supports zero-order-hold (order=0) and first-order-interpolation (order=1)
