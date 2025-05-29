```
mode_trajectory(sol::ParticleFilteringSolution)
mode_trajectory(x::AbstractMatrix, we::AbstractMatrix)
```

Compute the mode (particle with largest weight) along the trajectory of a particle-filter solution. Returns a matrix of size `T × nx`.
