```julia
finalize!(
    simulation::SpeedyWeather.AbstractSimulation
) -> Any

```

Finalize a `simulation`. Finishes the progress meter, unscales variables, finalizes the output, writes a restart file and finalizes callbacks.
