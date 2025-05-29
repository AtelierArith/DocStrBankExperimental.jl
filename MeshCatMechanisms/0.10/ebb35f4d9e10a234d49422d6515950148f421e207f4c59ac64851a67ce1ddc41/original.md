```
animate(mvis::MechanismVisualizer,
        times::Vector{Float64},
        configurations::Vector{Vector{Float64}};
        fps::Float64=60, realtimerate::Float64=1.)
```

Animate the given mechanism passing through a time-coded series of configurations by linearly interpolating the configuration vectors.
