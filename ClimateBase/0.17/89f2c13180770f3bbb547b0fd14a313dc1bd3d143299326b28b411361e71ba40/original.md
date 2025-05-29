```
realtime_days(t::AbstractVector{<:TimeType}, T = Float32)
```

Convert the given *sequential* date time vector `t` in a vector in a format of "real time", where time is represented by real numbers, increasing cumulatively, as is the case when representing a timeseries `x(t)`. As only differences matter in this form, the returned vector always starts from 0. The measurement unit of time here is days.

For temporal sampling less than daily return `realtime_milliseconds(t) ./ (24*60*60*1000)`.

Example:

```juliarepl
julia> t = Date(2004):Month(1):Date(2004, 6)
Date("2004-01-01"):Month(1):Date("2004-06-01")

julia> realtime_days(t)
6-element Vector{Float32}:
   0.0
  29.0
  60.0
  90.0
 121.0
 151.0
```
