```julia
initialize!(
    simulation::SpeedyWeather.AbstractSimulation;
    period,
    steps,
    output
) -> Any

```

Initializes a `simulation`. Scales the variables, initializes the output, stores initial conditions, initializes the progress meter feedback, callbacks and performs the first two initial time steps to spin up the leapfrogging scheme.
