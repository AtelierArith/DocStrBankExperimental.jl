```
interpolate(f_interp::Function, ts::AbstractTimeSeries, t::Real, indhint::Union{Nothing,Integer,<:RefValue{<:Integer}})
```

Single extrapolation at time t::Real, provide an indhint for faster searching
