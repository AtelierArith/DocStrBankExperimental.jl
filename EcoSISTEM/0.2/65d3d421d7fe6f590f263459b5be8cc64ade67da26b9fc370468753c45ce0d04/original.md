```
simulate_record_diversity!(storage::AbstractArray, eco::Ecosystem,
  times::Unitful.Time, interval::Unitful.Time,timestep::Unitful.Time,
  scenario::SimpleScenario, divfun::Function, qs::Float64)
```

Function to run an ecosystem, `eco` for specified length of times, `duration`, for a particular timestep, 'timestep', and time interval for a diversity to be calculated and recorded, `interval`. Optionally, there may also be a scenario by which the whole ecosystem is updated, such as removal of habitat patches.
