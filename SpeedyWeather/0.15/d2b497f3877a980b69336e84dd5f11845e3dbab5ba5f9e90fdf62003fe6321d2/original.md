```julia
activate!(
    simulation::SpeedyWeather.AbstractSimulation,
    tracers::SpeedyWeather.Tracer...
)

```

Activate a deactivated (=frozen) tracers in a simulation, which is a setting in `simulation.model` only.
