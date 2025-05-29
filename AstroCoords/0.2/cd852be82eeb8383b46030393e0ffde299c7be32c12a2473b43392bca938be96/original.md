```
Spherical{T} <: AstroCoord
```

Spherical Orbital Elements. 6D parameterziation of the orbit r - radius θ - in-plane angle ϕ - out-of-plane angle ṙ - instantaneous rate of change of radius θdot - instantaneous rate of change of θ ϕdot - instantaneous rate of change of ϕ

Constructors Spherical(r, θ, ϕ, ṙ, ω, Ω) Spherical(X::AbstractArray) Spherical(X::AstroCoord, μ::Number)
