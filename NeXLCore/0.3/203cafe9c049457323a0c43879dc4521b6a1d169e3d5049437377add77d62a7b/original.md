```
gun(::Type{T}, energy::Float64, width::Float64=1.0e-7, initial::Position=Position(0.0,0.0,-10.0), direction=Position(0.0,0.0,1.0)::T where {T <: Particle}
```

A helper to construct the initial `Particle` in a randomized Gaussian distribution.
