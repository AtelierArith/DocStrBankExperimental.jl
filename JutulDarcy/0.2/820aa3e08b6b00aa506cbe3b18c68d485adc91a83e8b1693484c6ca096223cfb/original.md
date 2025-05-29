```
plot_reservoir_simulation_result(model::MultiModel, res::ReservoirSimResult; wells = true, reservoir = true)
```

Plot a reservoir simulation result. If `wells=true` well curves will be shown interactively. If `reservoir=true` the reservoir quantities will be visualized in 3D. These options can be combined.
