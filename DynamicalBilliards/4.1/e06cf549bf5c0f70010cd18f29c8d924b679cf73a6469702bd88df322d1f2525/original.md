```julia
MagneticParticle(ic::AbstractVector{T}, ω::Real) # where ic = [x0, y0, φ0]
MagneticParticle(x0, y0, φ0, ω)
MagneticParticle(pos::SVector, vel::SVector, ω)
MagneticParticle(p::AbstractParticle, ω)
```

Create a *magnetic* particle with initial conditions `x0, y0, φ0` and angular velocity `ω`. It propagates as a circle instead of a line, with radius `1/abs(ω)`.

The field `current_cell` shows at which cell of a periodic billiard is the particle currently located.
