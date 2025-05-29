```julia
Particle(ic::Vector{T}) #where ic = [x0, y0, φ0]
Particle(x0, y0, φ0)
Particle(pos::SVector, vel::SVector)
```

Create a particle with initial conditions `x0, y0, φ0`. It propagates as a straight line.

The field `current_cell` shows at which cell of a periodic billiard is the particle currently located.
