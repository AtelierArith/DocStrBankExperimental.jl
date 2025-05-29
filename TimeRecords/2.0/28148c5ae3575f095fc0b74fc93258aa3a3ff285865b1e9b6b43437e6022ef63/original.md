```
integrate(ts::AbstractTimeSeries{T}, Δt::TimeInterval, indhint=firstindex(ts); order=0) where T <: Number
```

Integrate a timeseries over time interval Δt using either a trapezoid method (order=1) or a flat method (order=0)
