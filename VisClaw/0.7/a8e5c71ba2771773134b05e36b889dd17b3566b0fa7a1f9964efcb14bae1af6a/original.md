```
replaceunit!(fgmax::VisClaw.FGmax, unit::Symbol)
replaceunit!(gauge::VisClaw.Gauge, unit::Symbol)
replaceunit!(amrs::VisClaw.AMR, unit::Symbol)
replaceunit!(track::VisClaw.Track, unit::Symbol)
```

Time unit converter The second arg unit must be any one of :second, :minute, :hour, or :day.
