```
strictinterp(f_interp::Function, ts::AbstractTimeSeries, t::Real, indhint::Union{Nothing,Integer,<:RefValue{<:Integer}})
```

Single interpolation at time t::Real, provide an indhint for faster searching Will return TimeRecord{t, Missing} if t is not within the range of the timeseries
