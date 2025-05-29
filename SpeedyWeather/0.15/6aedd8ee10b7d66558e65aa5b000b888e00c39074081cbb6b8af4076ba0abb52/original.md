```julia
initialize!(
    L::SpeedyWeather.Leapfrog,
    model::SpeedyWeather.AbstractModel
)

```

Initialize leapfrogging `L` by recalculating the timestep given the output time step `output_dt` from `model.output`. Recalculating will slightly adjust the time step to be a divisor such that an integer number of time steps matches exactly with the output time step.
