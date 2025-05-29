```
integrate(ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Real}; order=1) where T
```

Returns a vector of N-1 integrals, bounded on the intervals of v with the following order options:      (order=0) which uses the Riemann integral     (order=1) which uses a trapezoidal integral
