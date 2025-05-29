```
SpokesTrajectory{T} <: AbstractTrajectory{T}
```

Typical Cartesian and radial trajectories have a lot in common: a readout can be described by a starting point in k-space and a Δk per sample point. To avoid code repetition, both type of trajectories are made a subtype of SpokesTrajectory such that some methods that would be the same for both trajectories otherwise are written for SpokesTrajectory instead.
