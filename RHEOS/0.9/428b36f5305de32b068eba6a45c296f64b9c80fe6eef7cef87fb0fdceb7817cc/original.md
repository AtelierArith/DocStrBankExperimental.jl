```
stressfunction(data::RheoTimeData, f::T) where T<:Function
stressfunction(f::T, data::RheoTimeData) where T<:Function
```

Returns a new `RheoTimeData` with stress values calculated by applying the function `f` to the time data of the parameter data.

Normally used with a `RheoTimeData` generated using the `timeline` function.
