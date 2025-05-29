```
averages(ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Real}; order=0) where T
```

Returns a vector of N-1 time-weigted averages between the intervals of vt using either      (order=0) which uses the Riemann integral     (order=1) which uses a trapezoidal integral
