```julia
deactivate!(
    simulation::SpeedyWeather.AbstractSimulation,
    tracers::SpeedyWeather.Tracer...
)

```

Deactivate a tracer in a simulation, which is a setting in `simulation.model` only.
