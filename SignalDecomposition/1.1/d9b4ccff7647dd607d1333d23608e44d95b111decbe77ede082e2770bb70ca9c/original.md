```
TimeAnomaly()
```

Decompose timeseries `s` into a **sum** `x + r` wher `x` is the same-time average and `r` is the anomalies. Each unique day+month combination in `t` is identified, and the values of `s` for each year that has this day+month combination are averaged. As a result, the time vector `t` must be `<:AbstractVector{<:TimeType}`.

This method is very common in climate science, referred to as simply "anomalies".
