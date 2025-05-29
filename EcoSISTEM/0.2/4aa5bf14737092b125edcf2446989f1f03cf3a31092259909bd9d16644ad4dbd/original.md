```
simulate!(eco::Ecosystem, times::Unitful.Time, timestep::Unitful.Time,
          cacheInterval::Unitful.Time, cacheFolder::String,
          scenario_name::String)
```

Function to run an ecosystem, `eco` for specified length of times, `duration`, for a particular timestep, 'timestep'. A cache interval and folder/file name  are specified for saving output.
