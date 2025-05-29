```
simulate_record!(eco::Ecosystem, duration::Unitful.Time, interval::Unitful.Time,
     timestep::Unitful.Time)
```

Function to run an ecosystem, `eco` for specified length of times, `duration`, for a particular timestep, 'timestep', and time interval for abundances to be recorded, `interval`. Optionally, there may also be a scenario by which the whole ecosystem is updated, such as removal of habitat patches.
