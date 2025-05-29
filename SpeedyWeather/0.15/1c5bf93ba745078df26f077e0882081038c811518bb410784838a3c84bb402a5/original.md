```julia
initialize!(
    scheduler::SpeedyWeather.Schedule,
    clock::SpeedyWeather.Clock
) -> SpeedyWeather.Schedule

```

Initialize a Schedule with a Clock (which is assumed to have been initialized). Takes both scheduler.every and scheduler.times into account, such that both periodic and events can be scheduled simulataneously. But execution will happen only once if they coincide on a given time step.
