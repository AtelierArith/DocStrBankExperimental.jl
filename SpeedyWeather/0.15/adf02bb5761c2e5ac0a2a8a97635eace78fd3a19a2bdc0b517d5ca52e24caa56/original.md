```julia
Schedule(times::Dates.DateTime...) -> SpeedyWeather.Schedule

```

A Schedule based on DateTime arguments, For two consecutive time steps i, i+1, an event is scheduled at i+1 when it occurs in (i,i+1].
