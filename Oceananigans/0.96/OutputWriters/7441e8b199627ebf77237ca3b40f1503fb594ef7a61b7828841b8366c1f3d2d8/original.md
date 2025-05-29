```
set!(model, filepath::AbstractString)
```

Set data in `model.velocities`, `model.tracers`, `model.timestepper.Gⁿ`, and `model.timestepper.G⁻` to checkpointed data stored at `filepath`.
