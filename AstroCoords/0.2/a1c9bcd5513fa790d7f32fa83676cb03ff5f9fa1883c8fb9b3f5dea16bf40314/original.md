```
Cylindrical{T} <: AstroCoord
```

Cylindrical Orbital Elements. 6D parameterziation of the orbit ρ - in-plane radius θ - in-plane angle z - out-of-plane distance ρdot - instantaneous rate of change of in-plsne radius θdot - instantaneous rate of change of θ ż - instantaneous rate of change of z

Constructors Cylindrical(r, θ, z, ṙ, θdot, ż) Cylindrical(X::AbstractArray) Cylindrical(X::AstroCoord, μ::Number)
