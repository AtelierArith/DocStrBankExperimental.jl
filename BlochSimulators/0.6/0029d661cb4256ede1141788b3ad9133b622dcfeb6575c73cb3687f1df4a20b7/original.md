```
phase_encoding!(magnetization, trajectory::AbstractTrajectory, parameters)
```

For each `::AbstractTrajectory`, a method should be added to this function if it does any kind of phase encoding (so far Cartesian only).
