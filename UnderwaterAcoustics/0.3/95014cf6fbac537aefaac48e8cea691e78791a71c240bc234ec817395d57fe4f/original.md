```
rays(pm::PropagationModel, tx1::AcousticSource, θ::Real, rmax)
```

Compute the rays from `tx1` launched at angle `θ` (or all angles in `θ`, if it is a vector). Returns an array of `RayArrival` datatypes. `rmax` is the maximum horizontal range in meters to track the rays over.
