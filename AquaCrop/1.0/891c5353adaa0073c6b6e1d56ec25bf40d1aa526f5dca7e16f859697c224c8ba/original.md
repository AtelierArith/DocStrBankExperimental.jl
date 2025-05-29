```
season_run!(cropfield::AquaCropField)
```

Updates the `cropfield` for all days in the current season

In case you upload the data using `NormalFileRun` or `TomlFileRun` and you indicate multiple seasons, it will only run the first season.

In case you upload the data using `NoFileRun` it runs the simulation from `Simulation_DayNr1` up to `Simulation_DayNrN`.
